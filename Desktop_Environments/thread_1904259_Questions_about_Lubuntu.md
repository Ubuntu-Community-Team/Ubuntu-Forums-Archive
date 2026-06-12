---
title: "Questions about Lubuntu"
date: 2012-01-04
forum: Desktop Environments
---

### Post by Flanmaster on 2012-01-04
My situation and then questions:    

I am a student of languages and switched to Ubuntu for it's ease of use while studying languages. (language select at login screen, including keyboard layout, language support in open/libre-office, and more.  Ubuntu is now user UNfriendly for students of language so I am looking for a different distro that will satify my needs.  

In the past I have preferred ubuntu over all for a variety of reasons in addition to the core reasons and for familiarity I'd like to stick to close as possible so Lubuntu might provide that opportunity.    

1) Will Lubuntu have language repositories that enable me to install multiple languages on system    

2) will Lubuntu continue to support "select language at login" in the login manager? (including keyboard layout    

3) will I have access to 3rd party drivers the same way I did in ubuntu in the sytem settings.  

4) will lubuntu be able to handle the additional applications that I will want to install, such as libreoffice, eternallands, gimp, blender3d, inkscape, planeshift, chromium-bsu, galaga, etc. IronHide optimus (opensource support for nvidia's hybrid optimus gpu system) etc.?  

I have an asus n53sv intel quad core intel/nvidia optimus hybrid gpu 3gb ram 500gb hd.  

Thank you.  

If this is not the correct Thread to ask these questions please inform me of the correct thread.  

Thank you again.

---

### Post by nothingspecial on 2012-01-04
Questions moved from the Lubuntu One Stop Thread to a thread of their own

> **Flanmaster said:**
> I have questions about Lubuntu. Is this the thread to ask them or do I need a different thread?    



No,  You will get a much broader response to your questions if you make your own thread rather than post at the end of a huge thread that most forum readers will not read. Please use the lubuntu prefix for your questions.

---

### Post by Flanmaster on 2012-01-04
> **nothingspecial said:**
> Questions moved from the Lubuntu One Stop Thread to a thread of their own



No,  You will get a much broader response to your questions if you make your own thread rather than post at the end of a huge thread that most forum readers will not read. Please use the lubuntu prefix for your questions.

what is lubuntu prefix

---

### Post by nothingspecial on 2012-01-04
When you start a thread and you are using lubuntu you can prefix the thread when you Choose your title. If you look at the Desktop Environments board you will see that I have added a lubuntu prefix to your thread :)

---

### Post by Rodney9 on 2012-01-04
> **Flanmaster said:**
> My situation and then questions:    

I am a student of languages and switched to Ubuntu for it's ease of use while studying languages. (language select at login screen, including keyboard layout, language support in open/libre-office, and more.  Ubuntu is now user UNfriendly for students of language so I am looking for a different distro that will satify my needs.  

In the past I have preferred ubuntu over all for a variety of reasons in addition to the core reasons and for familiarity I'd like to stick to close as possible so Lubuntu might provide that opportunity.    

1) Will Lubuntu have language repositories that enable me to install multiple languages on system    

2) will Lubuntu continue to support "select language at login" in the login manager? (including keyboard layout    

3) will I have access to 3rd party drivers the same way I did in ubuntu in the sytem settings.  

4) will lubuntu be able to handle the additional applications that I will want to install, such as libreoffice, eternallands, gimp, blender3d, inkscape, planeshift, chromium-bsu, galaga, etc. IronHide optimus (opensource support for nvidia's hybrid optimus gpu system) etc.?  

I have an asus n53sv intel quad core intel/nvidia optimus hybrid gpu 3gb ram 500gb hd.  

Thank you.  

If this is not the correct Thread to ask these questions please inform me of the correct thread.  

Thank you again.

1 & 2, Yes languages are installed and you can pick which at log-in.

3. Yes, Lubuntu is built on Ubuntu and comes with the same drivers.

4. You can install Libre Offce etc no problem, it depends on your PC, I'm sure yours will be ok.

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Flanmaster on 2012-02-01
I thought I would add a summary before marking this "solved".  I have lubuntu 32 bit installed on 3 machines now.  an older compaq presario v3000 laptop amd/nvidia, a newer Asus n53sv intel quad core nvidia optimus, and a new samsung, amd vision a6 quad core radeon agp  On the compaq I had to connect via hardwire and update the broadcom wireless driver but it is much better for this old machine.  Everything works well considering the age of the machine.  I have it only in english with most default software for lxde  on the Asus I have changed the file manager to thunar, installed firefox and all my graphics editing software and am testing each of them out.  I have also installed ironhide for optimus support and it works well.  I have installed multiple languages.  There are a few hiccups and handicaps IMO.  Even though I have multiple keyboards configured AND the keyboard changing app set up, I have to run a script on login to force the system to allow the app to change keyboards on the fly.  I also have to manually disable the touchpad with xinput.  For the most part I can do this with a shell script after log in simply double clicking and selecting "execute" but sometimes the webcam grabs the id for the touchpad so I have to use "xinput -list" to verify it's still on the same channel before running the script.  These are the biggest issues.  I can select a specific language on login but still have to use the system wide keyboard until I get logged in and run the script to allow the keyboard changing.  I could set up separate accounts for each language and set each one to the appropriate keyboard and language but this takes up space that I want to use for other things.  I had to change the file manager to thunar because the default kept crashing and would not order by name.   on the Samsung I have an atheros wireless and still have not figured out how to get the drivers to recognize in lubuntu.  I have opened a separate thread for that.  On a whole I can do some of what I want with Lubuntu, certainly more than the newer Ubuntu will allow.  It is definitely faster, and with the right configuration I can run most all the same applications I could under the older ubuntu which had the language support I really wanted.  So all in all, Lubuntu is a really good operating system so far, but has a few issues.  I might have to change linux flavors on the samsung if I cannot resolve the atheros driver issues but hopefully not.  If I do find a different flavor that will provide the language support I am looking for I will have to try it out, but I am hoping that Ubuntu/Lubuntu will add it back in.  Thanks For all the responses.

---

