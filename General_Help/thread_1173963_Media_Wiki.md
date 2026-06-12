---
title: "Media Wiki"
date: 2009-05-30
forum: General Help
---

### Post by stSpringer2003 on 2009-05-30
Hi All,
I have installed Mediawiki on my thumb drive useing Windows XP and following the instructions on this link

[http://mihirknows.blogspot.com/2009/02/run-your-personal-wiki-from-usb-stick.html](http://mihirknows.blogspot.com/2009/02/run-your-personal-wiki-from-usb-stick.html)

It works fine.

I would like to do the same in Ubuntu. Plug in my USB to a Ubuntu box and run Mediawiki from the thumb drive.

Has anyone got a clue on how to do this?

Thanks

---

### Post by geraldvillorente on 2009-05-30
just do the same thing...if you already installed your web server on your USB then just start your web server something like this
```

sudo /media/USB_directory_name/xampp/xampp start

```
hope im corect...I never tried this before...:D

---

### Post by stSpringer2003 on 2009-05-30
> **geraldvillorente said:**
> just do the same thing...if you already installed your web server on your USB then just start your web server something like this
```

sudo /media/USB_directory_name/xampp/xampp start

```
hope im corect...I never tried this before...:D

Thanks for your reply. 

In Ubuntu when I plug in my USB I see Corsair on the Ubuntu Desktop this is my thumb drive. The file I run in windows is xampp-control.exe This starts the xampp control panel which gives you the options to start or stop apache and mySQL. After starting both apache and mysql i can then go to my web browser 
and type in

 [http://localhost/wiki/index.php/Special:UserLogin](http://localhost/wiki/index.php/Special:UserLogin)
whick brings up my login screen. I then type in my password and my web page is displayed.

can you explain what I would plug in to 
sudo /media/USB_directory_name/xampp/xampp start

---

### Post by geraldvillorente on 2009-05-30
Obviously you're using window-based xampp which is not cross-platform... the .exe extension won't work in Linux unless you have a wine installed on your system...Try lampp its a linux-based Apache/MySQL/PHP similar to xampp...

BTW, why do you want to use USB as your webroot? I think it is not practical as we all know that Flash drive is not durable/stable compare to HDD. Just an opinion...

---

