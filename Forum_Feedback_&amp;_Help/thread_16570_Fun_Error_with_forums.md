---
title: "Fun Error with forums"
date: 2005-02-22
forum: Forum Feedback &amp; Help
---

### Post by hamiltjr on 2005-02-22
When trying to link my avatar to a URL, I received the following error...

Warning: feof(): supplied argument is not a valid stream resource in /includes/functions_upload.php on line 120

Warning: fread(): supplied argument is not a valid stream resource in /includes/functions_upload.php on line 122

Warning: feof(): supplied argument is not a valid stream resource in /includes/functions_upload.php on line 120

Warning: fread(): supplied argument is not a valid stream resource in /includes/functions_upload.php on line 122

Warning: feof(): supplied argument is not a valid stream resource in /includes/functions_upload.php on line 120

Warning: fread(): supplied argument is not a valid stream resource in /includes/functions_upload.php on line 122

Warning: feof(): supplied argument is not a valid stream resource in /includes/functions_upload.php on line 120

Warning: fread(): supplied argument is not a valid stream resource in /includes/functions_upload.php on line 122

Warning: feof(): supplied argument is not a valid stream resource in /includes/functions_upload.php on line 120

Warning: fread(): supplied argument is not a valid stream resource in /includes/functions_upload.php on line 122

etc... etc.. it just repeats. Looks like an infinite loop!

---

### Post by kassetra on 2005-02-22
Ooooh, ok, I'll let the admin know... thank you for reporting this issue!

---

### Post by ubuntu-geek on 2005-02-22
what was the format of the url you entered? I cant seem to reproduce this error.

---

