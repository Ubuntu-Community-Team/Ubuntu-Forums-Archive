---
title: "shell_exec in PHP script"
date: 2009-06-25
forum: General Help
---

### Post by patdundee on 2009-06-25
Hi Guys
Extremely new to UBUNTU just moving off windows servers but getting there slowly
 
 
UBUNTU 8.10 server
 
I have a mail server installed and I cannot get one of its commands to run from PHP page
 
I am running the latest PHP 
 
I have the following code 
 
$output1=shell_exec("tellmail add_domain test2.com");;
echo "<pre>$output1</pre>";
 
and the result is this
 
Could not determine permissions (/path/to/command/displayed here) Permission denied - must be root to run tellmail
 
PHP is not running in safe mode
 
What do I have to do / change to allow my web page to run the above command
 
Many thanks in advance
 
Patdundee

---

### Post by patdundee on 2009-06-25
Figured it out 
 
For those who have the same issue this and cannot get shell_exec to work from a web interface this worked for me
 
edit the file /etc/sudoers
 
add this line
www-data ALL= NOPASSWD: /path/to/your/executable/filename
 
Save the file
 
Place these 2 lines in your PHP page to run the file and view the output
 
$output1=shell_exec("sudo /path/to/your/executable/filename");
echo "<pre>$output1</pre>";
 
 
Hope this helps others with similar issues
 
:D
 
Patdundee

---

