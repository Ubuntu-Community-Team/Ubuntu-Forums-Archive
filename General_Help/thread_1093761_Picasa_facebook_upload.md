---
title: "Picasa facebook upload"
date: 2009-03-11
forum: General Help
---

### Post by pasha07 on 2009-03-11
Hey, 

I am running Ubuntu 8.10 and Picasa 3.0. I followed the instruction on this site:

[http://nawsher.wordpress.com/2008/05/28/upload-pictures-to-facebook-from-picasa-ubuntu/](http://nawsher.wordpress.com/2008/05/28/upload-pictures-to-facebook-from-picasa-ubuntu/)

and installed the facebook upload button. 

Everything works great (Sign on facebook, give album name, etc) then I click upload and get this message:

[http://www.facebook.com/album.php?aid=____&id=______](http://www.facebook.com/album.php?aid=____&id=______)

it creates the folder, but doesn't upload the files. Anyone knows how I can fix this?

Thanks,

---

### Post by sheshdd on 2009-03-12
i'm installing it right now from a .deb file.i'll let you know if it worked for me.

---

### Post by LazarusHC on 2009-03-21
I'm having this issue, too.  Any help would be appreciated.

---

### Post by Crowchild on 2009-03-25
I am having the same problem as well.

---

### Post by AlexOslo on 2009-05-01
Same.

---

### Post by archiesteel on 2009-05-11
Same for me. Apparently the developer of the facebook upload button is aware of this...

From the [FAQ]("http://apps.facebook.com/picasauploader/faq.php"):

> **I'm using Linux. Can I use the uploader?**

Unfortunately, the Linux version of Picasa does not properly support web-based plugins like this one. I am looking into creating a desktop-based plugin for Linux users, but I do not currently have anything available. Please check back occasionally for status updates.

I guess we're stuck until either Google gets their act together, or this guy manages to write a special Linux plugin...don't hold your breath, this could take awhile! :(

---

### Post by timpalpant on 2009-06-28
It doesn't work because WINE has a bug in its HTTP libraries. The solution for me was to install Picasa and Internet Explorer under the same WINE root. This way Picasa uses the IE libraries and the Facebook plugin works correctly.

---

### Post by frenzie on 2009-07-06
> **timpalpant said:**
> It doesn't work because WINE has a bug in its HTTP libraries. The solution for me was to install Picasa and Internet Explorer under the same WINE root. This way Picasa uses the IE libraries and the Facebook plugin works correctly.

Hi Timpalpant

Would you be able to describe how you installed IE under the same WINE root that picasa uses?

---

### Post by schwascore on 2009-07-20
> **timpalpant said:**
> It doesn't work because WINE has a bug in its HTTP libraries. The solution for me was to install Picasa and Internet Explorer under the same WINE root. This way Picasa uses the IE libraries and the Facebook plugin works correctly.

I also can not get this to work.  I tried both IE8 and Firefox 3.5 and both fail during install.

---

### Post by nidelius on 2009-09-07
Alright, preknowldge ~ = /home/yourusername/
Here is how to do it

Open a terminal and..

wget [http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz](http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz)
tar zxvf ies4linux-latest.tar.gz
cd ies4linux-*
./ies4linux
you get an error
run ./ies4linux again
you get another error
run ./ies4linux again
It should now say that you've installed IE4 and that it's exacutable is in ~/bin/ie6

Notice that there is a new wine root installed in ~/.ies4linux/ie6
AHA :)

NOW download the WINDOWS VERSION OF PICASA!!! to your ~/.ies4linux/ie6/drive_c folder

as of now that is: [http://dl.google.com/picasa/picasa3-setup.exe](http://dl.google.com/picasa/picasa3-setup.exe)

Alright, now you have to start the setup within the ~/.ies4linux/ie6 root environment. How?

Open a terminal and copy and paste (shift+insert) the following command and edit so it fits your system

env WINEPREFIX="/home/user/.ies4linux/ie6" wine "C:\picasa3-setup.exe"

DONT FORGET TO CHANGE user to YOUR username

Now run through the setup then check
~/.ies4linux/ie6/drive_c/Program files/google/Picasa3/
is it there? good then you have done it right otherwise start over..

now go here
[http://apps.facebook.com/picasauploader/faq.php?#installation](http://apps.facebook.com/picasauploader/faq.php?#installation)

or use this link

[http://webkinesis.com/fbpicasa/packages/v2/facebook_v2.pbz](http://webkinesis.com/fbpicasa/packages/v2/facebook_v2.pbz)

to download the facebook plugin download it to 

~/.ies4linux/ie6/drive_c/Program Files/Google/Picasa3/buttons
clean up your mess that you extracted and downloaded before
rm -rf ies4linux*

Then start Picasa!!!
env WINEPREFIX="/home/user/.ies4linux/ie6" wine "C:\Program files\Google\Picasa3\Picasa3.exe"

DONT forget to change user to YOUR username

Now run Picasa you should see the facebook icon in picasa!!

Mark and upload your pictures..
Picasa will hang half the times but it will always upload your pictures to facebook!!

to close the ****** up hanged picasa use 
pkill -9 wineserver

---

### Post by jakobb on 2009-09-27
Perfect guide
I even got Picasa 3.5 working

---

### Post by arasbm on 2009-10-12
Thank you for the workaround, I was finally able to get picasa's facebook button to work, by following your procedure. My fiancée is very happy! :P. 
I am using Kubuntu 9.10 beta.

---

### Post by ias on 2009-10-22
Thank you. Great. Not at all easy for a non techie, but it works. Actually, firefox tried to block me downloading the ie tar file -- said it was some sort of toxic website.. but i went ahead.

The big problem was that it doesn't recognise all my photos. It showed only the files in the root of the Pictures directory, although under the Folder Manager all the subfolders with my many pictures are set to 'Scan Always'. 

I finally figured it out: you have to go to Z: (the linux root) and dig for your home/pictures folder and set that to be scanned. Don't know why this works, but it does..

One day, let's hope these fb and picasa guys will make this a one click operation.

Thank you!

---

### Post by yipeecaiey on 2009-10-26
Until such time as the google geeks or the picasa fb plugin developer do solve this issue for those of us using linux...I found a workaround that does not require installing anything additional but does take an additional step each time I upload albums to facebook.


[LIST=1]
[*]I use picasa on my ubuntu desktop to manage photos and albums (installed through synaptec)
[*]I create picasaweb albums through the native picasa interface that does work (and runs very smoothly in the background)
[*]I enabled the 'photo 2 photo' facebook application [http://apps.facebook.com/flickrtophotos/](http://apps.facebook.com/flickrtophotos/).  This app will manually import photos of your choosing into facebook.  Note: this is an additional step, but the pics DO end up in native fb albums rather than other picasa-fb apps that seem to always come just short of that.
[/LIST]
Hope that helps!

---

### Post by BFG on 2010-06-09
I was trying to achieve this and found this thread.  I found an easy fix:
[http://www.facebook.com/topic.php?uid=2483740875&topic=16487](http://www.facebook.com/topic.php?uid=2483740875&topic=16487)

I've got v3.0 running on 9.10 via the test repos. and this works.

---

### Post by tommawat on 2010-11-17
Hello.  I have been trying to get picasa on my linux box to upload photos to facebook.  Never worked with the linux picasa version for me however.

Solution:

1. install wine 1.2.1 (current version from synaptic, based on beta apparently...)

2. go to picasa.google.com and download the Windows version picasa 3.8, NOT the linux version 3 beta (which is older and lacks new features).  

3. make the picasa .exe file able to be run as a programme (right click, properties, permissions and check the box to allow to be run as a programme) then right click it and open with wine.  it will install fine. 

4. install the picasa uploader button from the site: [http://apps.facebook.com/picasauploader/](http://apps.facebook.com/picasauploader/) 
(if it won't automatically do it, just do it manually and download the button file and place it into the wine's C drive google picasa button folder usually at C:\Program Files\Google\Picasa3\buttons then close and restart picasa).

Using the button:

1. open picasa 3.8 from wine, select a photo

2. press the newly visible facebook button at the bottom, it will automatically open your default browser (for me it opens Chrome for Linux which I already had installed from add/remove programmes or synaptic, outside of wine as any normal programme)

3. follow the instructions in the browser (it will ask about new or previous folders as the new destination for your upload); when you are finished it will eventually tell you it was successful.  you can click to view it in your facebook album where you will need to approve it since it was uploaded by third party app and not by facebook itself.  for me this gives a 'sorry' error which i just close and wait and the photo and new album appear exactly as they should with no problem.  i am not sure why there is a fake 'sorry' error, as it uploaded every time for me, even with multiple photos.

Also, the email through gmail works as well if you are a fan like me.

I run Ubuntu 10.10 with Gnome on a Dell Inspiron Mini.  While all of this was installed, I had already on my computer Picasa for linux 3.  I left it there and there were no disruptions and they can both be run if you desire at the same time.  I think i will uninstall the 3.0 for linux and only use the wine windows version 3.8 as the facebook button works unlike for the linux 3.0 version which does not support buttons well.

I have tried using Shotwell and Fspot and Digikam but to me they are ugly.  

Good luck...

---

