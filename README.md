
<?php

include __DIR__ . '/config/koneksi.php';


$query = mysqli_query(
    $conn,
    "SELECT * FROM ekstrakurikuler LIMIT 1"
);


$data = mysqli_fetch_assoc($query);



if (!$data) {

    die("Data ekstrakurikuler belum tersedia.");

}


$jadwal = explode("\n", $data['jadwal']);

$prestasi = explode("\n", $data['prestasi']);

?>


<!DOCTYPE html>
<html lang="id">


<head>


    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">


    <title>
        Ekstrakurikuler
        <?= $data['nama_sekolah']; ?>
    </title>



    <link rel="stylesheet" href="/sekolahku/assets/css/style.css">



    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">


    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">


</head>



<style>
    * {

        margin: 0;
        padding: 0;
        box-sizing: border-box;

        font-family: 'Poppins', sans-serif;

    }



    body {

        background: #f5f7fa;

    }



    /* HERO */

    .ekskul-hero {


        padding: 140px 20px;


        text-align: center;


        color: white;


        background:


            linear-gradient(135deg,
                #064d45,
                #0b6b61);


    }



    .ekskul-hero h1 {


        font-size: 65px;

        margin-bottom: 20px;


    }


    .ekskul-hero p {


        font-size: 20px;

        max-width: 850px;

        margin: auto;


    }





    /* STAT */

    .stats {


        padding: 80px 0;


    }


    .stats-container {


        width: 90%;

        max-width: 1200px;

        margin: auto;


        display: grid;

        grid-template-columns: repeat(4, 1fr);

        gap: 25px;


    }


    .stat-card {


        background: white;

        padding: 35px;


        border-radius: 25px;


        text-align: center;


        box-shadow:

            0 10px 30px rgba(0, 0, 0, .08);


    }


    .stat-card i {


        font-size: 40px;

        color: #0b6b61;

        margin-bottom: 15px;


    }


    .stat-card h2 {


        font-size: 40px;

        color: #0b6b61;


    }





    /* TITLE */


    .section-title {


        text-align: center;

        margin-bottom: 60px;


    }


    .section-title h2 {


        font-size: 45px;

        color: #0b6b61;


    }


    .section-title p {


        color: #6b7280;

        margin-top: 10px;


    }







    /* EKSKUL UNGGULAN */


    .ekskul-section {


        width: 90%;

        max-width: 1200px;

        margin: auto;

        padding-bottom: 100px;


    }



    .ekskul-item {


        display: flex;

        align-items: center;

        gap: 50px;

        margin-bottom: 80px;


    }



    .ekskul-item.reverse {


        flex-direction: row-reverse;


    }



    .ekskul-img {


        flex: 1;

    }



    .ekskul-img img {


        width: 100%;

        height: 350px;

        object-fit: cover;

        border-radius: 25px;


        box-shadow:

            0 15px 35px rgba(0, 0, 0, .1);


    }



    .ekskul-content {


        flex: 1;


    }



    .ekskul-content h3 {


        font-size: 38px;

        color: #0b6b61;

        margin-bottom: 20px;


    }



    .ekskul-content p {


        line-height: 2;

        color: #64748b;


    }







    /* JADWAL */


    .jadwal {


        padding: 100px 0;

        background: white;


    }


    .timeline {


        width: 80%;

        margin: auto;


    }


    .timeline-item {


        display: flex;

        gap: 25px;


        padding: 25px;


        margin-bottom: 20px;


        background: #f8fafc;


        border-radius: 20px;


    }


    .hari {


        width: 120px;

        font-weight: 700;

        color: #0b6b61;


    }






    /* GALERI */


    .galeri {


        padding: 100px 0;


    }



    .galeri-grid {


        width: 90%;

        max-width: 1200px;

        margin: auto;


        display: grid;

        grid-template-columns: repeat(4, 1fr);

        gap: 20px;


    }



    .galeri-item img {


        width: 100%;

        height: 250px;

        object-fit: cover;

        border-radius: 20px;


    }







    /* PRESTASI */


    .prestasi {


        padding: 100px 0;

        background: white;


    }



    .prestasi-container {


        width: 90%;

        max-width: 1200px;

        margin: auto;


    }



    .prestasi-card {


        background: #f8fafc;

        padding: 25px;

        border-radius: 20px;

        margin-bottom: 20px;

        display: flex;

        gap: 20px;


    }



    .prestasi-card i {


        font-size: 40px;

        color: #f59e0b;


    }







    @media(max-width:900px) {


        .stats-container {


            grid-template-columns: 1fr;


        }



        .ekskul-item,
        .ekskul-item.reverse {


            flex-direction: column;


        }



        .galeri-grid {


            grid-template-columns: 1fr;


        }



        .ekskul-hero h1 {


            font-size: 40px;


        }


    }
</style>





<body>



    <?php include 'components/navbar.php'; ?>





    <section class="ekskul-hero">


        <h1>

            Ekstrakurikuler

        </h1>


        <p>

            <?= $data['deskripsi']; ?>

        </p>


    </section>









    <section class="stats">


        <div class="stats-container">



            <div class="stat-card">

                <i class="fa-solid fa-users"></i>

                <h2>
                    <?= $data['jumlah_peserta']; ?>
                </h2>

                <p>Peserta Aktif</p>

            </div>




            <div class="stat-card">

                <i class="fa-solid fa-trophy"></i>

                <h2>
                    <?= $data['jumlah_prestasi']; ?>
                </h2>

                <p>Prestasi</p>

            </div>




            <div class="stat-card">

                <i class="fa-solid fa-star"></i>

                <h2>
                    <?= $data['jumlah_ekskul']; ?>
                </h2>

                <p>Ekstrakurikuler</p>

            </div>




            <div class="stat-card">

                <i class="fa-solid fa-user-tie"></i>

                <h2>
                    <?= $data['jumlah_pembina']; ?>
                </h2>

                <p>Pembina</p>

            </div>



        </div>

    </section>








    <section class="ekskul-section">


        <div class="section-title">

            <h2>
                Ekstrakurikuler Unggulan
            </h2>


            <p>
                Kegiatan pengembangan minat dan bakat siswa
            </p>


        </div>






        <?php for ($i = 1; $i <= 4; $i++): ?>


            <div class="ekskul-item <?= $i % 2 == 0 ? 'reverse' : ''; ?>">



                <div class="ekskul-img">


                    <img src="/sekolahku/assets/images/<?= $data['foto_ekskul' . $i]; ?>">


                </div>





                <div class="ekskul-content">


                    <h3>

                        <?= $data['judul_ekskul' . $i]; ?>

                    </h3>



                    <p>

                        <?= $data['deskripsi_ekskul' . $i]; ?>

                    </p>



                </div>



            </div>



        <?php endfor; ?>



    </section>








    <section class="jadwal">


        <div class="section-title">

            <h2>

                Jadwal Kegiatan

            </h2>

        </div>





        <div class="timeline">


            <?php foreach ($jadwal as $j):


                $pecah = explode("|", $j);


                ?>



                <div class="timeline-item">


                    <div class="hari">

                        <?= $pecah[0]; ?>

                    </div>


                    <div>

                        <?= $pecah[1] ?? ''; ?>

                    </div>


                </div>



            <?php endforeach; ?>



        </div>


    </section>









    <section class="galeri">


        <div class="section-title">

            <h2>

                Galeri Kegiatan

            </h2>


        </div>





        <div class="galeri-grid">


            <?php for ($i = 1; $i <= 4; $i++): ?>


                <div class="galeri-item">


                    <img src="/sekolahku/assets/images/<?= $data['galeri' . $i]; ?>">


                </div>


            <?php endfor; ?>


        </div>


    </section>









    <section class="prestasi">


        <div class="section-title">

            <h2>

                Prestasi Ekstrakurikuler

            </h2>

        </div>




        <div class="prestasi-container">



            <?php foreach ($prestasi as $p): ?>


                <div class="prestasi-card">


                    <i class="fa-solid fa-trophy"></i>


                    <div>

                        <?= $p; ?>

                    </div>


                </div>


            <?php endforeach; ?>



        </div>


    </section>







    <?php include 'components/footer.php'; ?>



</body>

</html>
<?php

include __DIR__ . '/config/koneksi.php';


$query = mysqli_query(
   $conn,
   "SELECT * FROM fasilitas LIMIT 1"
);


$data = mysqli_fetch_assoc($query);


if (!$data) {

   die("Data fasilitas belum tersedia.");

}

?>


<!DOCTYPE html>
<html lang="id">

<head>

   <meta charset="UTF-8">

   <meta name="viewport" content="width=device-width, initial-scale=1.0">


   <title>
      Fasilitas <?= $data['nama_sekolah']; ?>
   </title>


   <link rel="stylesheet" href="/sekolahku/assets/css/style.css">


   <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">


   <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">


</head>



<style>
   * {

      margin: 0;
      padding: 0;
      box-sizing: border-box;
      font-family: 'Poppins', sans-serif;

   }


   body {

      background: #f5f7fa;

   }



   /* HERO */


   .fasilitas-hero {


      padding: 130px 20px;


      text-align: center;


      color: white;


      background:

         linear-gradient(135deg,
            #064d45,
            #0b6b61);


   }


   .fasilitas-hero h1 {


      font-size: 60px;

      margin-bottom: 20px;


   }


   .fasilitas-hero p {


      font-size: 20px;

      max-width: 850px;

      margin: auto;

      opacity: .9;


   }





   /* STAT */


   .fasilitas-stats {


      width: 90%;

      max-width: 1200px;

      margin: -70px auto 80px;


      display: grid;

      grid-template-columns: repeat(4, 1fr);

      gap: 25px;


      position: relative;


   }



   .stat-box {


      background: white;


      padding: 35px;


      border-radius: 25px;


      text-align: center;


      box-shadow:
         0 15px 35px rgba(0, 0, 0, .08);


   }



   .stat-box i {


      font-size: 40px;

      color: #0b6b61;

      margin-bottom: 15px;


   }



   .stat-box h2 {


      font-size: 40px;

      color: #0b6b61;


   }






   /* TITLE */


   .section-title {


      text-align: center;

      margin-bottom: 60px;


   }



   .section-title h2 {


      font-size: 45px;

      color: #0b6b61;


   }



   .section-title p {


      color: #6b7280;

      margin-top: 10px;


   }







   /* FASILITAS */


   .fasilitas-section {


      width: 90%;

      max-width: 1200px;

      margin: auto;

      padding-bottom: 100px;


   }



   .fasilitas-item {


      display: flex;

      align-items: center;

      gap: 50px;

      margin-bottom: 80px;


   }



   .fasilitas-item.reverse {


      flex-direction: row-reverse;


   }



   .fasilitas-img {


      flex: 1;

   }



   .fasilitas-img img {


      width: 100%;

      height: 350px;

      object-fit: cover;

      border-radius: 25px;


   }



   .fasilitas-content {


      flex: 1;

   }



   .fasilitas-content h3 {


      font-size: 38px;

      color: #0b6b61;

      margin-bottom: 20px;


   }



   .fasilitas-content p {


      line-height: 2;

      color: #64748b;


   }





   /* GALERI */


   .gallery {


      background: white;

      padding: 100px 0;


   }



   .gallery-grid {


      width: 90%;

      max-width: 1200px;

      margin: auto;


      display: grid;

      grid-template-columns: repeat(4, 1fr);

      gap: 20px;


   }



   .gallery-item img {


      width: 100%;

      height: 260px;

      object-fit: cover;

      border-radius: 20px;


   }







   /* LINGKUNGAN */


   .lingkungan {


      padding: 100px 0;


   }



   .lingkungan-grid {


      width: 90%;

      max-width: 1200px;

      margin: auto;


      display: grid;

      grid-template-columns: repeat(4, 1fr);

      gap: 25px;


   }



   .lingkungan-card {


      background: white;

      padding: 35px;

      border-radius: 25px;

      text-align: center;


      box-shadow:

         0 10px 30px rgba(0, 0, 0, .08);


   }



   .lingkungan-card i {


      font-size: 40px;

      color: #0b6b61;

      margin-bottom: 20px;


   }





   @media(max-width:900px) {


      .fasilitas-stats,
      .gallery-grid,
      .lingkungan-grid {


         grid-template-columns: 1fr;


      }



      .fasilitas-item,
      .fasilitas-item.reverse {


         flex-direction: column;


      }


      .fasilitas-hero h1 {


         font-size: 40px;


      }



   }
</style>




<body>




   <?php include 'components/navbar.php'; ?>





   <section class="fasilitas-hero">


      <h1>

         Fasilitas Sekolah

      </h1>


      <p>

         <?= $data['deskripsi']; ?>

      </p>


   </section>






   <section class="fasilitas-stats">



      <div class="stat-box">

         <i class="fa-solid fa-school"></i>

         <h2><?= $data['ruang_kelas']; ?></h2>

         <p>Ruang Kelas</p>

      </div>




      <div class="stat-box">

         <i class="fa-solid fa-book"></i>

         <h2><?= $data['perpustakaan']; ?></h2>

         <p>Perpustakaan</p>

      </div>




      <div class="stat-box">

         <i class="fa-solid fa-computer"></i>

         <h2><?= $data['lab']; ?></h2>

         <p>Lab Komputer</p>

      </div>




      <div class="stat-box">

         <i class="fa-solid fa-futbol"></i>

         <h2><?= $data['lapangan']; ?></h2>

         <p>Lapangan</p>

      </div>



   </section>







   <section class="fasilitas-section">


      <div class="section-title">

         <h2>

            Fasilitas Unggulan

         </h2>


         <p>

            Sarana terbaik untuk mendukung pembelajaran

         </p>


      </div>





      <div class="fasilitas-item">


         <div class="fasilitas-img">

            <img src="/sekolahku/assets/images/<?= $data['foto_fasilitas1']; ?>">

         </div>



         <div class="fasilitas-content">


            <h3>

               <?= $data['judul_fasilitas1']; ?>

            </h3>


            <p>

               <?= $data['deskripsi_fasilitas1']; ?>

            </p>


         </div>


      </div>







      <div class="fasilitas-item reverse">


         <div class="fasilitas-img">


            <img src="/sekolahku/assets/images/<?= $data['foto_fasilitas2']; ?>">


         </div>



         <div class="fasilitas-content">


            <h3>

               <?= $data['judul_fasilitas2']; ?>

            </h3>


            <p>

               <?= $data['deskripsi_fasilitas2']; ?>

            </p>


         </div>


      </div>





   </section>







   <section class="gallery">


      <div class="section-title">

         <h2>

            Galeri Fasilitas

         </h2>


      </div>




      <div class="gallery-grid">



         <?php for ($i = 1; $i <= 4; $i++): ?>


            <div class="gallery-item">


               <img src="/sekolahku/assets/images/<?= $data['galeri' . $i]; ?>">


            </div>


         <?php endfor; ?>



      </div>


   </section>







   <section class="lingkungan">


      <div class="section-title">

         <h2>

            Lingkungan Sekolah

         </h2>


      </div>





      <div class="lingkungan-grid">



         <div class="lingkungan-card">

            <i class="fa-solid fa-tree"></i>

            <h4><?= $data['lingkungan1']; ?></h4>

            <p>Lingkungan nyaman dan hijau.</p>

         </div>




         <div class="lingkungan-card">

            <i class="fa-solid fa-shield"></i>

            <h4><?= $data['lingkungan2']; ?></h4>

            <p>Area sekolah aman.</p>

         </div>





         <div class="lingkungan-card">

            <i class="fa-solid fa-heart"></i>

            <h4><?= $data['lingkungan3']; ?></h4>

            <p>Mendukung perkembangan siswa.</p>

         </div>





         <div class="lingkungan-card">

            <i class="fa-solid fa-star"></i>

            <h4><?= $data['lingkungan4']; ?></h4>

            <p>Fasilitas terus berkembang.</p>

         </div>



      </div>



   </section>







   <?php include 'components/footer.php'; ?>





</body>

</html>
<?php
echo password_hash("admin123", PASSWORD_DEFAULT);
?>
<?php

include __DIR__ . '/config/koneksi.php';


$query = mysqli_query(
  $conn,
  "SELECT * FROM identitas LIMIT 1"
);


$profil = mysqli_fetch_assoc($query);


if (!$profil) {

  die("Data identitas sekolah belum tersedia.");

}

?>


<!DOCTYPE html>

<html lang="id">


<head>


  <meta charset="UTF-8">

  <meta name="viewport" content="width=device-width, initial-scale=1.0">


  <title>
    <?= $profil['nama_sekolah']; ?>
  </title>



  <link rel="stylesheet" href="/sekolahku/assets/css/style.css">



  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">



  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">



  <style>
    * {

      margin: 0;
      padding: 0;
      box-sizing: border-box;

      font-family: 'Poppins', sans-serif;

    }



    body {

      background: #f5f7fa;

    }




    /* HERO */


    .profile-hero {


      padding: 130px 20px;


      text-align: center;


      color: white;


      background:

        linear-gradient(135deg,
          #064d45,
          #0b6b61);


    }



    .profile-badge {


      display: inline-flex;

      align-items: center;

      gap: 10px;


      padding: 12px 25px;


      border-radius: 50px;


      background: rgba(255, 255, 255, .15);


      margin-bottom: 25px;


    }



    .profile-hero h1 {


      font-size: 60px;

      margin-bottom: 15px;


    }



    .profile-hero p {


      font-size: 20px;

      opacity: .85;


    }







    /* CONTENT */


    .profile-section {


      padding: 90px 20px;


    }



    .profile-container {


      width: 90%;

      max-width: 1200px;

      margin: auto;


    }



    .profile-card {


      background: white;


      border-radius: 30px;


      overflow: hidden;


      box-shadow:

        0 15px 40px rgba(0, 0, 0, .08);


    }




    .profile-header {


      padding: 35px;


      display: flex;


      align-items: center;


      gap: 25px;


      background:

        linear-gradient(135deg,
          #065f56,
          #0b6b61);


      color: white;


    }



    .profile-icon {


      width: 75px;

      height: 75px;


      border-radius: 20px;


      display: flex;


      align-items: center;


      justify-content: center;


      background: rgba(255, 255, 255, .15);


      font-size: 35px;


    }



    .profile-header h2 {


      font-size: 36px;


    }







    .profile-body {


      padding: 45px;


    }



    .profile-grid {


      display: grid;


      grid-template-columns: 1fr 1fr;


      gap: 40px;


    }




    .info-item {


      display: flex;


      gap: 18px;


      margin-bottom: 30px;


    }



    .info-icon {


      width: 55px;

      height: 55px;


      border-radius: 16px;


      display: flex;


      align-items: center;


      justify-content: center;


      background: #e8faf6;


      color: #0b6b61;


      font-size: 22px;


      flex-shrink: 0;


    }



    .info-text small {


      color: #6b7280;


      font-weight: 700;


    }



    .info-text h4 {


      font-size: 22px;

      margin-top: 5px;


    }



    .info-text p {


      color: #64748b;

      line-height: 1.8;


    }



    .info-text a {


      text-decoration: none;

      color: #0b6b61;


    }




    .map-btn {


      display: inline-flex;


      align-items: center;


      gap: 10px;


      margin-top: 15px;


      padding: 12px 25px;


      background: #0b6b61;


      border-radius: 15px;


      color: white !important;


    }







    /* TAMBAHAN */


    .additional-info {


      margin-top: 40px;


      border-top: 1px solid #eee;


      padding-top: 35px;


    }




    .additional-grid {


      display: grid;


      grid-template-columns: repeat(3, 1fr);


      gap: 25px;


    }




    .additional-card {


      background: #f8fafc;
      padding: 25px;
      border-radius: 20px;
    }




    .additional-card i {


      font-size: 30px;


      color: #0b6b61;


      margin-bottom: 15px;


    }




    .additional-card h4 {


      font-size: 24px;


      margin-top: 10px;


    }






    @media(max-width:900px) {



      .profile-grid,
      .additional-grid {


        grid-template-columns: 1fr;


      }



      .profile-header {


        flex-direction: column;


        text-align: center;


      }



      .profile-hero h1 {


        font-size: 40px;


      }


    }
  </style>


</head>




<body>



  <?php include 'components/navbar.php'; ?>






  <section class="profile-hero">


    <div class="profile-badge">


      <i class="fa-solid fa-school"></i>


      Profil Sekolah


    </div>




    <h1>

      Identitas Sekolah

    </h1>



    <p>

      <?= $profil['nama_sekolah']; ?>

    </p>



  </section>







  <section class="profile-section">


    <div class="profile-container">


      <div class="profile-card">





        <div class="profile-header">


          <div class="profile-icon">


            <i class="fa-solid fa-school"></i>


          </div>




          <div>


            <h2>

              <?= $profil['nama_sekolah']; ?>

            </h2>



            <p>

              NPSN :
              <?= $profil['npsn']; ?>

            </p>


          </div>


        </div>







        <div class="profile-body">



          <div class="profile-grid">





            <div>



              <div class="info-item">


                <div class="info-icon">

                  <i class="fa-solid fa-user"></i>

                </div>



                <div class="info-text">


                  <small>
                    Kepala Sekolah
                  </small>



                  <h4>

                    <?= $profil['nama_kepsek']; ?>

                  </h4>


                </div>


              </div>







              <div class="info-item">


                <div class="info-icon">

                  <i class="fa-solid fa-phone"></i>

                </div>



                <div class="info-text">


                  <small>

                    Telepon

                  </small>


                  <h4>


                    <a href="tel:<?= $profil['telepon']; ?>">


                      <?= $profil['telepon']; ?>


                    </a>


                  </h4>


                </div>


              </div>








              <div class="info-item">


                <div class="info-icon">


                  <i class="fa-solid fa-envelope"></i>


                </div>



                <div class="info-text">


                  <small>

                    Email

                  </small>


                  <h4>


                    <a href="mailto:<?= $profil['email']; ?>">


                      <?= $profil['email']; ?>


                    </a>


                  </h4>


                  <p>


                    <a href="<?= $profil['website']; ?>" target="_blank">


                      <?= $profil['website']; ?>


                    </a>


                  </p>


                </div>


              </div>



            </div>







            <div>


              <div class="info-item">


                <div class="info-icon">


                  <i class="fa-solid fa-location-dot"></i>


                </div>



                <div class="info-text">


                  <small>

                    Alamat

                  </small>


                  <p>


                    <?= nl2br($profil['alamat']); ?>


                  </p>




                  <a href="<?= $profil['maps']; ?>" target="_blank" class="map-btn">


                    <i class="fa-solid fa-map"></i>


                    Lihat Maps


                  </a>



                </div>



              </div>


            </div>





          </div>







          <div class="additional-info">


            <h3>

              <i class="fa-solid fa-circle-info"></i>

              Informasi Tambahan


            </h3>




            <br>




            <div class="additional-grid">





              <div class="additional-card">


                <i class="fa-solid fa-school"></i>


                <p>Status Sekolah</p>


                <h4>

                  <?= $profil['status_sekolah']; ?>

                </h4>


              </div>






              <div class="additional-card">


                <i class="fa-solid fa-award"></i>


                <p>Akreditasi</p>


                <h4>

                  <?= $profil['akreditasi']; ?>

                </h4>


              </div>







              <div class="additional-card">


                <i class="fa-solid fa-calendar"></i>


                <p>Tahun Berdiri</p>


                <h4>

                  <?= $profil['tahun_berdiri']; ?>

                </h4>


              </div>




            </div>


          </div>





        </div>


      </div>


    </div>


  </section>






  <?php include 'components/footer.php'; ?>



</body>


</html>
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <title>Website Sekolah</title>

    <!-- CSS -->
    <link rel="stylesheet" href="/sekolahku/assets/css/style.css">

    <!-- FONT -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600;700&display=swap" rel="stylesheet">

    <link rel="stylesheet"
    href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">

    <!-- Animasi Masuk_keluar -->
    <link rel="stylesheet"
    href="https://unpkg.com/aos@2.3.4/dist/aos.css"/>

</head>
<body>

<script src="https://unpkg.com/aos@2.3.4/dist/aos.js"></script>

<script>
  AOS.init({
    duration: 1200,
    easing: 'ease-in-out',
    once: false,
    mirror: true
  });
</script>

<!-- NAVBAR -->
<?php include 'components/navbar.php'; ?>

<!-- HERO -->
<?php include 'components/hero.php'; ?>

<!-- STATS -->
<?php include 'components/stats.php'; ?>

<!-- SAMBUTAN -->
<?php include 'components/sambutan.php'; ?>

<!-- VISI MISI -->
<?php include 'components/visi.php'; ?>

<!-- KONTAK -->
<?php include 'components/kontak.php'; ?>

<!-- FOOTER -->
<?php include 'components/footer.php'; ?>

<!-- JS -->
<script src="/sekolahku/assets/js/main.js" defer></script>

</body>
</html>
<?php

include __DIR__ . '/config/koneksi.php';


$query = mysqli_query(
    $conn,
    "SELECT * FROM sejarah LIMIT 1"
);


$sejarah = mysqli_fetch_assoc($query);



if (!$sejarah) {

    die("Data sejarah sekolah belum tersedia.");

}


?>


<!DOCTYPE html>

<html lang="id">


<head>


    <meta charset="UTF-8">

    <meta name="viewport" content="width=device-width, initial-scale=1.0">


    <title>

        <?= $sejarah['nama_sekolah']; ?>

    </title>



    <link rel="stylesheet" href="/sekolahku/assets/css/style.css">



    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700&display=swap" rel="stylesheet">



    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css">





    <style>
        * {

            margin: 0;

            padding: 0;

            box-sizing: border-box;

            font-family: 'Poppins', sans-serif;

        }



        body {

            background: #f5f7fa;

        }



        /* HERO */


        .sejarah-hero {


            padding: 130px 20px;


            text-align: center;


            color: white;


            background:

                linear-gradient(135deg,

                    #064d45,

                    #0b6b61);


        }




        .sejarah-badge {


            display: inline-flex;


            align-items: center;


            gap: 10px;


            padding: 12px 25px;


            border-radius: 50px;


            background: rgba(255, 255, 255, .15);


            margin-bottom: 25px;


        }



        .sejarah-hero h1 {


            font-size: 60px;


            margin-bottom: 15px;


        }



        .sejarah-hero p {


            font-size: 20px;


            opacity: .9;


        }







        /* CONTENT */


        .sejarah-section {


            padding: 100px 20px;


        }



        .sejarah-container {


            width: 90%;

            max-width: 1100px;

            margin: auto;


        }




        .sejarah-card {


            background: white;


            border-radius: 30px;


            padding: 45px;


            margin-top: -80px;


            position: relative;


            box-shadow:

                0 15px 40px rgba(0, 0, 0, .08);


        }






        .sejarah-header {


            display: flex;


            align-items: center;


            gap: 25px;


            margin-bottom: 35px;


        }




        .sejarah-icon {


            width: 75px;


            height: 75px;


            border-radius: 20px;


            display: flex;


            align-items: center;


            justify-content: center;


            background: #e8faf6;


            color: #0b6b61;


            font-size: 35px;


        }





        .sejarah-header h2 {


            font-size: 36px;


            color: #0b6b61;


        }



        .sejarah-header p {


            color: #64748b;


        }





        /* TAHUN */


        .tahun-box {


            background:

                linear-gradient(135deg,

                    #064d45,

                    #0b6b61);


            color: white;


            padding: 30px;


            border-radius: 25px;


            text-align: center;


            margin-bottom: 35px;


        }




        .tahun-box p {


            font-size: 18px;


        }



        .tahun-box h3 {


            font-size: 50px;


        }







        /* ISI SEJARAH */


        .sejarah-text {


            font-size: 18px;


            line-height: 2;


            color: #64748b;


            text-align: justify;


        }





        @media(max-width:768px) {


            .sejarah-hero h1 {


                font-size: 40px;


            }



            .sejarah-card {


                padding: 30px;


            }



            .sejarah-header {


                flex-direction: column;


                text-align: center;


            }



        }
    </style>



</head>




<body>



    <?php include 'components/navbar.php'; ?>






    <section class="sejarah-hero">



        <div class="sejarah-badge">


            <i class="fa-solid fa-landmark"></i>


            Sejarah Sekolah


        </div>





        <h1>


            Perjalanan Sekolah


        </h1>



        <p>


            <?= $sejarah['nama_sekolah']; ?>


        </p>



    </section>









    <section class="sejarah-section">



        <div class="sejarah-container">



            <div class="sejarah-card">





                <div class="sejarah-header">



                    <div class="sejarah-icon">


                        <i class="fa-solid fa-school"></i>


                    </div>





                    <div>


                        <h2>


                            <?= $sejarah['nama_sekolah']; ?>


                        </h2>



                        <p>


                            Sejarah dan perkembangan sekolah


                        </p>


                    </div>



                </div>







                <div class="tahun-box">


                    <p>


                        Tahun Berdiri


                    </p>



                    <h3>


                        <?= $sejarah['tahun_berdiri']; ?>


                    </h3>



                </div>







                <div class="sejarah-text">


                    <?= nl2br($sejarah['sejarah']); ?>


                </div>





            </div>



        </div>



    </section>







    <?php include 'components/footer.php'; ?>




</body>


</html>
