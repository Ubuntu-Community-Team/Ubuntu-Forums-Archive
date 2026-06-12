---
title: "Web based file sharing"
date: 2009-04-13
forum: General Help
---

### Post by taget on 2009-04-13
Hello, i am looking for a web based file sharing/repository for my and me co workers to log into remotely. i have a 1 and 1 shared linux server. so far google has failed me, well i failed at googling. i was hoping for something that you could log into and upload download files, i tried phpfilesadmin and it had no login feature. boxroom i dont think will work as i cant install software directly on the server and it had some dependencies that im not sure would be satisfied. does anyone have any suggestions.

thanks in advance 
taget

---

### Post by mb_webguy on 2009-04-13
Downloading files from a web site is simple, and [limiting access with a password]("http://www.addedbytes.com/apache/password-protect-a-directory-with-htaccess/") is only slightly more complicated.

Uploading files can be done with an HTML form and a small PHP script.  For example, the following files would allow users to upload jpeg files up to 350KB in size to a subdirectory called "upload" in directory containing the files, using the password "swordfish".  

Save the following HTML as "upload.html":```
<html>
<body>
  <form enctype="multipart/form-data" action="upload.php" method="post">
    <input type="hidden" name="MAX_FILE_SIZE" value="1000000" />
    Choose a file to upload: <input name="uploaded_file" type="file" />
    Password: <input name="password" type="password" />
    <input type="submit" value="Upload" />
  </form>
</body>
</html>
```Save the following code as "upload.php".```
<?php
//&#1057;heck that the password is correct before proceeding
if ($_POST["password"] != 'swordfish')
{
  die('Error: Incorrect password!');
}
//Check that we have a file
if ((!empty($_FILES["uploaded_file"])) && ($_FILES['uploaded_file']['error'] == 0)) {
  //Check if the file is JPEG image and it's size is less than 350Kb
  $filename = basename($_FILES['uploaded_file']['name']);
  $ext = substr($filename, strrpos($filename, '.') + 1);
  if (($_FILES["uploaded_file"]["type"] == "image/jpeg") && 
    ($_FILES["uploaded_file"]["size"] < 350000)) {
    //Determine the path to which we want to save this file
      $newname = dirname(__FILE__).'/upload/'.$filename;
      //Check if the file with the same name is already exists on the server
      if (!file_exists($newname)) {
        //Attempt to move the uploaded file to it's new place
        if ((move_uploaded_file($_FILES['uploaded_file']['tmp_name'],$newname))) {
           echo "It's done! The file has been saved as: ".$newname;
        } else {
           echo "Error: A problem occurred during file upload!";
        }
      } else {
         echo "Error: File ".$_FILES["uploaded_file"]["name"]." already exists";
      }
  } else {
     echo "Error: Only .jpg images under 350Kb are accepted for upload";
  }
} else {
 echo "Error: No file uploaded";
}
?>
```
Now, if you're using an .htaccess file to password protect the "upload" directory using the password "swordfish", anyone who knows the password can upload jpeg files to or download files from the "upload" directory.

Modifying the script to allow for other file types of various sizes is a fairly simple matter.  For example, the following modification will also allow the upload of gif files of 350KB, and Word documents up to 500KB.```
[...]
  //Check if the file is JPEG or GIF image of less than 350KB, or a Word document of less than 500KB
  $filename = basename($_FILES['uploaded_file']['name']);
  $ext = substr($filename, strrpos($filename, '.') + 1);
  if ([COLOR="Blue"](([/COLOR]($_FILES["uploaded_file"]["type"] == "image/jpeg")[COLOR="Blue"] || ($_FILES["uploaded_file"]["type"] == "image/gif"))[/COLOR] 
    && ($_FILES["uploaded_file"]["size"] < 350000)[COLOR="Blue"]) || (($_FILES["uploaded_file"]["type"] == "application/msword") &&($_FILES["uploaded_file"]["size"] < 500000))[/COLOR]) {
[...]
```

Note that the upload size limit for a default LAMP installation on Ubuntu is 2MB.  You can change this by editing the value of the upload_max_filesize in the /etc/php5/apache2/php.ini file.  You may also have to make a few minor edits to the Apache configuration files, but I'm not sure.  You'll have to restart Apache with "sudo /etc/init.d/apache2 restart" for these changes to take effect.

---

