---
title: "i know nothing about php"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Joseph Elliott on 2006-09-10
I am including a survey on the website i am creating and am using code for the form that requires a php file to submit the form.  I have no idea on how to create a php file or if i even need it(come to think of it im not sure what php is).  I guess all i really want is for the info from the form to be emailed to me, if thats not possible collecting in a file on the site somewhere would be ok to.  If you need to see the code im using just let me know and ill post it.

---

### Post by lagagnon on 2006-09-10
It is very bad form to expect anyone to write code for you, but we are happy to help you write it. Google found me this in 3 seconds of work:
[http://phpfmg.sourceforge.net/home.php](http://phpfmg.sourceforge.net/home.php)

---

### Post by Vinze on 2006-09-10
Well if you are sure your webserver can handle PHP then you can just insert the following in an HTML file:

```
<?php

mail('youremailaddress@yourdomain.org', 'Subject', $_POST['text_field_name'], 'From: noreply@nonexistent.org');

?>

```

Then change the extension of that file from html to php and set it as the "action" of the form (action="file.php").

---

