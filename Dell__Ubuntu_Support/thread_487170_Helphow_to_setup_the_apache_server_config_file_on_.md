---
title: "Help:::how to setup the apache server config file on linux ubuntu ?"
date: 2007-06-28
forum: Dell  Ubuntu Support
---

### Post by a_kalash on 2007-06-28
Hello,

I am using Linux (Ubuntu7.04 Desktop Edition) as an operating system and i did the installation of apache server 2.2.4 to create a local web server and it's running <it works> but i don't have any idea about the instructions or commands that must be change in the config file of apache in order to let the server share the file from the appropriate directory (where the data is exicted)??

If anyone knows how to set up this config file and can provide it to me i will appreciate his or her help!!

Thanks

---

### Post by neptho on 2007-06-28
This isn't really a Dell specific question, but you will find the settings for your default apache configuration in /etc/apache2/

Sites which are available ar ein /etc/apache2/sites-available.  Sites which you have ENABLED (turned on) should be symlinked to  /etc/apache2/sites-enabled

You will see a 00-default; that is the default, and unless you are going to use name based virtualhosts, you shoulld be able to make all changes to this file, then run 'sudo /etc/init.d/apache2 restart'

---

