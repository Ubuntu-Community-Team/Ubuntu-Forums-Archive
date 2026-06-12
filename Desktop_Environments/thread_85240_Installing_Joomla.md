---
title: "Installing Joomla"
date: 2005-11-02
forum: Desktop Environments
---

### Post by Snorrie on 2005-11-02
Greetings,

I want to install the content-management-system Joomla on my Ubuntu 5.10. The main reasons are to learn this system and creating websites (although I don't have a webspace yet so I want to design them local). I have no experience with php, apache, mysql. So I don't know what I can do with them or what I need etc. 
So I was hoping that someone has a complete tutorial/howto how I can install Joomla.

Thnx,
Snorrie

---

### Post by ad noiseam on 2005-11-06
Same question here.

I am new to Linux, and don't know my way with Php, MySql or Apache. On Windows, some application install this all for you, so that people can focus on working on a CMS site. I guess that things are a bit more complicated in Linux.

Does anybody care to explain how you get from a clean Ubuntu install to a site where you can install a CMS locally, something where mysql and php work, and where you can find something at "localhost".

Sorry for being so ignorant.

---

### Post by ad noiseam on 2005-11-08
I have solved this, so I might just let people know.

First, go to this [Wiki article](https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=(mysql)) and do everything as written there. The only part that didn't work for me was "Securing Apache".

Then, download Joomla from their website, and decompress it. Copy the files to /var/www (you might have to do this as a root user, which means type "sudo nautilus" in a terminal).

Go to your browser, and go to [http://localhost](http://localhost). You should see the beginning of the installation of Joomla. If you need to change permissions, go to /var/www, right click on the folder, and change the permissions.

I just did all this, and it works, I have Joomla installed locally here.

---

