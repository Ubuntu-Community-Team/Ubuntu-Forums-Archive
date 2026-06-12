---
title: "please for the love of all things holy, someone make youtube work for me!!!"
date: 2008-12-07
forum: Desktop Environments
---

### Post by shogunmidas on 2008-12-07
i know that it has already been talked about in a thread on here but i went through them and tried to fix it and nothing.

ive tried a ton of fixes and nothing. every time i try and watch anything on youtube it tells me "Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player."

can anyone out there help me through this one? i would be eternally grateful.

---

### Post by keithld on 2008-12-07
Which web browser are you using & do you have Javascript enabled in it???

---

### Post by shogunmidas on 2008-12-07
im using Firefox/3.0b5

but... how do i tell if i have javascript enabled?

---

### Post by keithld on 2008-12-07
In Firefox go to:

edit > Preferences > Click on the "Content Tab" and look at lines 3 & 4 and see if they have a check mark next to them....

---

### Post by johnn1949 on 2008-12-07
All I did to get video to work was install "ubuntu-restricted-extras" in synaptic package manager, and it all worked.

---

### Post by shogunmidas on 2008-12-07
i do have java enabled, box lines 3 and 4 are checked.

but i got this version of ubuntu 8.04 out of "the official ubuntu book 3rd edition" which is good but i suppose a little old.

i guess i should update to 8.10 and then see if it works?

---

### Post by keithld on 2008-12-07
You can also ask here for a solution and see what they say...

[Firefox Support](http://forums.mozillazine.org/viewforum.php?f=38)

---

### Post by sigurnjak on 2008-12-07
You can try older version of flash from here :
[http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/)

 Newer version didnt work well for me on youtube or facebook . I am using 
flashplugin-nonfree_9.0.124.0ubuntu2_i386.deb. 

good luck!

---

### Post by shogunmidas on 2008-12-08
ok i finished installing the new version of ubuntu 8.10.

so lets begin. im ready. someone make it do. make youtube work again. please.

---

### Post by shogunmidas on 2008-12-09
my friend sent me this fix and after installing 8.10 and doing the fix youtube is working fine now. if anyone else out there is having this problem i hope this helps.

   1. Open /etc/apt/sources.list:

      sudo nano /etc/apt/sources.list

   2. Add the following lines to the end of the file:

      deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe
      deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe

      deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
      deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

      deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
      deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

   3. Now close save the file and close nano by doing the following: hit "Ctrl+X" and then "y" and then "Enter"
   
   4.Run:

      sudo apt-get update

You should now be able to install such software as "gnome-art" and many others.


then:
Easily install the Macromedia Flash Plugin for Firefox

   1. Run the following command:

      sudo apt-get install flashplugin-nonfree
          

   2. Restart Firefox and flash should now be working. Note: Websites requiring Flash 8 will not work because there is not a version 8 of Macromedia Flash for Linux yet.

---

### Post by sigurnjak on 2008-12-09
Are you sure adding dapper repo to ibex is a good idea ?

---

### Post by lnogueir on 2008-12-09
Did you use No-script Firefox extension?

Did you install flash player?

---

### Post by slick666 on 2008-12-09
I've got everything working but when the flash player is running it will randomly crash when I'm at the following sites:

[http://www.joost.com/]("http://www.joost.com/")
[http://www.fancast.com/]("http://www.fancast.com/")
[http://www.youtube.com/]("http://www.youtube.com/")

I'm trying to convince someone to switch to FOSS but if there computer is crashing as much as it did before it's doesn't speak well of ubuntu despite the fact that it is a non-free component. Any ideas on what to do or how to debug this one?

---

### Post by sigurnjak on 2008-12-10
i have tried all your links and all seem to work with my set up . I use most recent ff3 from repo and flash 9 from here  [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/) . I use 9.0 r 124 . Make sure you first uninstall flash 10 .

---

### Post by slick666 on 2008-12-10
I'm not sure it's flash any more. Firefox crashed when I only had this web site up. I went into synaptic and reinstall everything labeled firefox. So far so good.

---

