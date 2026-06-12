---
title: "php file is not uploading on ubuntu 10.10"
date: 2011-03-11
forum: Desktop Environments
---

### Post by manishdhr on 2011-03-11
i have installed LAMP server on my ubuntu 10.10
i am having problem in uploading files

upload form
<html>
<body>
<form action="tmp.php" method="post"
enctype="multipart/form*data">
<label for="file">Filename:</label>
<input type="file" name="file" id="file" /> 
<br />
<input type="submit" name="submit" value="Submit" />
</form>
</body>
</html>


tmp.php

<?php

   var_dump($_FILES)
?>


output- array(0) { }  

i am not able to upload image files

plz help

---

### Post by SeijiSensei on 2011-03-11
Have you carefully read this section of the PHP manual yet? 

[http://www.php.net/manual/en/features.file-upload.php](http://www.php.net/manual/en/features.file-upload.php)

File uploads are very tricky.  It took a couple of hours to get everything worked out the first time I set this up.  I would only recommend you trying this approach if you're a somewhat experienced PHP coder with a good understanding of how things like the $_FILES global works. You'll also need to be prepared to handle file permission issues since the uploads will be owned by web server user, like the "www-data" user that Apache runs as.

If you just want to be able to upload files, services like FTP, Samba, or WebDAV might be easier to implement.

---

### Post by manishdhr on 2011-03-11
thanx for reading my question ,
my problem is solved
i have hidden character in my upload code which was the problem, it was not visible but when i looked in source code in browser i found it.

(copy past from pdf);-

<form action="tmp.php" method="post" enctype="multipart/form*-data">
<input type="file" name="ufile"  /> 
<input type="submit" value="Upload" />
</form>



(copy paste from php.net):-

<form action="tmp.php" method="post" enctype="multipart/form-data">
<input type="file"  name="ufile" />
<input type="submit" value="Upload" />
</form> 

both the codes are different, i was editing in gedit(it wasnt showing any difference)

---

### Post by manishdhr on 2011-03-11
here it is showing a star in that place
anyways thanx, its my stupidity

---

