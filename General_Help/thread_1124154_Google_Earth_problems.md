---
title: "Google Earth problems"
date: 2009-04-13
forum: General Help
---

### Post by SilverFrost on 2009-04-13
When i try to start Google Earth a rong message comes up and tells me:

It didnt work to create the catalog:
/root/.googleearth/Cache

Then its followed by a second rong message:

It didnt work to write current cache to My places. Values are given as follow:

Pathway to My places: "/home/myusername/.googleearth"
Cachecatalog: "/home/myusername/.googleearth/Cache

Then i click OK and the Google Earth splash screen comes up and it crashes right after??

How do i make this work?

Thanks.

---

### Post by vk_rams on 2009-04-13
Hey if you have installed google earth from command 
sudo apt-get install googleearth

this is really a problematic, it will crash in the middle. 

I don't know how to debug this. But i solved this issue by doing the below steps

1. First remove the googleearth by sudo apt-get remove googleearth
2. Download Google earth from below URL
[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)
After downloading give execute permission to the downloaded binary file, By chmod 777 GoogleEarth.bin or do it graphically

Now you are ready to install the google earth

This will work fine without any crash. Try it...

---

### Post by Lunx on 2009-04-13
I suggest uninstalling GE, enabling the medibuntu repository and then install using synaptic. I had all kinds of troubles, including the same error as yourself, and this is the only method I've found to work reliably for me.

I'll also post something which I wrote in another thread as it should help you get it all working nicely once installed.

> **Lunx said:**
> Having torn my hair out following all the advice and mis-advice I could findon getting GE to run, I can vouch that the suggestion from Phuilinux in post #2 up there ^ is the best way of getting it installed (medibuntu repository has v5 beta ). Make sure that step one is to follow the advice about enabling the Medibutu repository

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then once that is done you can find the package in Synaptic and install as usual.

I have found that every version of GE I've tried runs very buggy (if at all) when first started, but have worked out with advice cobbled together from several sources how I can get it to run. First of all, if it is playing up when you first try it, close GE and then switch from Compiz to Metacity. Restart GE and it should look better but it will probably now run as if half frozen, if this is the case you need to go to **View** in the GE menu and disable the **Atmosphere** setting and now hopefully all is good with the worlds again (both your own and Google's).

And remember to switch Compiz back on after, or you'll be wondering what happened to your effects :p.

Real PITA needing to use work arounds like this, hope Google get their act together and get this Linux version sorted (didn't I hear half of Google staff use Ubuntu? They must staff who don't use GE...)

Edit: I should have mentioned I tried this install method only about half an hour before writing this post and it worked well in Jaunty


You can find the thread here

[http://ubuntuforums.org/showthread.php?t=1114219](http://ubuntuforums.org/showthread.php?t=1114219)

---

### Post by SilverFrost on 2009-04-13
> **vk_rams said:**
> Hey if you have installed google earth from command 
sudo apt-get install googleearth

this is really a problematic, it will crash in the middle. 

I don't know how to debug this. But i solved this issue by doing the below steps

1. First remove the googleearth by sudo apt-get remove googleearth
2. Download Google earth from below URL
[http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)
After downloading give execute permission to the downloaded binary file, By chmod 777 GoogleEarth.bin or do it graphically

Now you are ready to install the google earth

This will work fine without any crash. Try it...



I tried to uninstall it by:

```
sudo apt-get remove googleearth

E: Could not find package: googleearth


```

It doesnt work to uninstall/remove?

---

### Post by Lunx on 2009-04-13
> **vk_rams said:**
> 

1. First remove the googleearth by sudo apt-get remove googleearth


Yep, that's how I'd do it and then you could also run

```
sudo apt-get autoremove
```

and that will get rid of all the packages that Google Earth relied on but are no longer needed

---

### Post by Lunx on 2009-04-13
> **SilverFrost said:**
> I tried to uninstall it by:

```
sudo apt-get remove googleearth

E: Could not find package: googleearth


```It doesnt work to uninstall/remove?

Maybe something didn't get installed properly at the outset. The original error you had has to do with permissions of who owns the file and seems to occur when you download from Google and use gdebi to install, should be pointing at /home rather that /root. Try having a look to see if there are files in the following places* /usr/bin *should have a file in it, and there should be a directory in *usr/share*. Once a user runs GE, there should also be a hidden directory in their home directory eg. a *.googleearth*  folder. Have a look in those places and see what's there, you could probably try to remove manually

FWIW, I installed GE again just now since I didn't have it. Did it via the command line by enabling Medibuntu and then used apt-get install. Took no more than five minute by the time I downloaded and agreed to terms of use

---

### Post by thewolfman on 2009-04-13
Hi chaps,

just to add my tuppence worth, I have an old PC with an ATI Radeon 9600 graphics card and found that I can only get Google Earth to work with version 4.0 which I got as a deb package from:
 [http://www.geekconnection.org/downloads.htm](http://www.geekconnection.org/downloads.htm)

So try that if you have an older PC and you cannot get version 5 to work.

Happy Easter

---

### Post by SilverFrost on 2009-04-13
The whole Google Earth installation was in the /opt folder.
I remove it from /opt manually and then reinstall it?

---

### Post by Lunx on 2009-04-13
> **SilverFrost said:**
> The whole Google Earth installation was in the /opt folder.
I remove it from /opt manually and then reinstall it?

Just had a look in my /opt directory and there's nothing there, so if that's the only directory you can find then you could remove it and then install with the directions I posted earlier. Also see if it managed to create a .*googleearth* directory in your desktop (go to desktop directory and Ctrl+h to see hidden files and folders)

---

### Post by SilverFrost on 2009-04-13
I removed the googleearth directory from /opt.
Then i reinstalled it from Synaptic, a package in Synaptic called:

googleearth-package  0.5.4  utility to automatically build a Debian package of Google 
Earth.

Because this was the only package viewed in the repo. I dont know if its rong?
Btw, after installing it it came no icon to start it from on the gnome panel?
How do i start it?

---

### Post by vk_rams on 2009-04-14
For your information, Please dont use the googleearth from debian or dapper. Download it from google and install it

---

### Post by SilverFrost on 2009-04-14
Why is that? Something rong with the Google Earth in Intrepid´s repo?
That was just that... it crash everytime when i launch it when install it from  own Google's page:

> It didnt work to create the catalog:
/root/.googleearth/Cache


Followed by:

> Pathway to My places: "/home/myusername/.googleearth"
Cachecatalog: "/home/myusername/.googleearth/Cache

I have try to install it without root rights also.

---

### Post by SilverFrost on 2009-04-16
I complete erase all early installs of Google Earth in Ubuntu and starting over with:

Added the Medibuntu repo from: [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
then > sudo apt-get install googleearth wich installs an early verison from the repo, but *still* it refuse to launch. It starts in like 2,3 seconds and then crash?
So now no matter where i install it from the Google Earth page or Medibuntu repo it doesnt start as it should.

---

### Post by El Viejo Lobo on 2009-05-04
For a sluggish GE worked for me TO GO TO "VIEW"  AND TAKE OUT "ATMOSPHERE" 

**THANKES**

---

