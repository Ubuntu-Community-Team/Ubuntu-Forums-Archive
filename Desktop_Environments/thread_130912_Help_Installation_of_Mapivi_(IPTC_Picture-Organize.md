---
title: "Help: Installation of Mapivi (IPTC Picture-Organizer) &amp; Tk::JPEG"
date: 2006-02-15
forum: Desktop Environments
---

### Post by philxxx on 2006-02-15
Hi,

I switched from Mac OS X to Ubuntu a few weeks ago after my iBook died and went through a steep learning curve :-)
I've succesfully updated most important apps, tried KDE (and witched back to GNOME) but now I'm stucked with the installation of Mapivi.

Mapivi ([http://mapivi.sourceforge.net/mapivi.shtml](http://mapivi.sourceforge.net/mapivi.shtml)) is an opensource picture manager that supports IPTC metadata.

Under Mac OS X and Windows there are different applications available, but it seems that mapivi is the only program that really supports IPTC - very important for me.

Unfortunately I'm unable to get a running mapivi-system on my Ubuntu v5.10.
I think I've read every manual and stumbled through a lot of posts asking for help.

Before I post the error messages I got, I would like to ask if there is ANYBODY out there who is using mapivi on ubuntu or who can point me to another application supporting IPTC metadata?

Following the installation requirements for mapivi, it seems that the problem is that I can't get  Tk::JPEG module installed. 

So to sum up:
1) has anybody installed Tk::JPEG on Ubuntu and can post a short howto?
2) has anybody installed mapivi?

I like linux, but I can't believe that there is no soulution for picture organizing using ITPC-metadata...

regards from berlin / germany

p hil

---

### Post by Martin-Herrmann on 2006-05-02
Hi,

you should install the newest version of Perl/Tk ([http://search.cpan.org/~ni-s/Tk-804.027/]("http://search.cpan.org/~ni-s/Tk-804.027/")). 
This version includes Tk::JPEG.
Following these steps: unzip, unpack, perl Makefile.PL, make, make test, sudo make install.
I had to install several other packages using apt-get (cc, gcc, X11-Include files etc.) on my Ubuntu v5.10 first.
Please drop me an email if you need further assistance.

Regards,
  Martin - Author of Mapivi

---

### Post by Martin-Herrmann on 2006-05-02
Hi again,

I repeated the Mapivi installation on another Ubuntu 5.10 system today.
Here are the steps needed.

First, to install Perl-Tk you need some other packages:
> sudo apt-get install make
> sudo apt-get install libx11-dev
> sudo apt-get install gcc
> sudo apt-get install build-essential
> sudo apt-get install libncourses5-dev   (I'm not really sure if this is needed)
> sudo apt-get install libstdc++6-dev     (I'm not really sure if this is needed)

Then download Perl/Tk ([http://search.cpan.org/~ni-s/Tk-804.027/]("http://search.cpan.org/~ni-s/Tk-804.027/")), unzip and unpack it and change to the unpacked directory Tk-804-027.
Then:
> perl Makefile.PL
> make
> make test (some tests may fail, that's no problem)
> sudo make install

Now Perl-Tk is installed.

The next step is to install two more Perl modules.
Download
[http://search.cpan.org/~bettelli/Image-MetaData-JPEG-0.15/]("http://search.cpan.org/~bettelli/Image-MetaData-JPEG-0.15/") and
[http://search.cpan.org/~tels/Image-Info-1.21/]("http://search.cpan.org/~tels/Image-Info-1.21/")

For each unzip, unpack and enter into the directory and do
> perl Makefile.PL
> make
> make test
> sudo make install

Now you should be able to start Mapivi by simply typing
> mapivi
in the mapivi directory.
If it is working you may copy mapivi to e.g. /usr/local/bin/.

You may later add the optional modules:
[http://search.cpan.org/~xpix/Tk-ResizeButton-0.01/]("http://search.cpan.org/~xpix/Tk-ResizeButton-0.01/")
[http://search.cpan.org/~whom/Tk-MatchEntry-0.4/]("http://search.cpan.org/~whom/Tk-MatchEntry-0.4/")
with the same procedure like described above.

Regards, Martin

---

### Post by Martin-Herrmann on 2006-06-01
Warning!

Perl/Tk 804.027 has a  bug, all Perl/Tk apps crash with a segfault when run
alongside GTK apps, when a GTK version later than 2.8.0 is used. 

But here is the bug description and a bug fix:
[https://launchpad.net/distros/ubuntu/+source/perl/+bug/27261]("https://launchpad.net/distros/ubuntu/+source/perl/+bug/27261")

Here is a brief description how I applied the bug fix:
[http://ubuntuforums.org/showthread.php?t=76684&highlight=perl%2Ftk+gnome]("http://ubuntuforums.org/showthread.php?t=76684&highlight=perl%2Ftk+gnome")

Since applying that patch my Perl/Tk applications no longer crash when starting Gnome or GTK applications, like Nautilus, GIMP, etc.!

Regards, Martin

---

### Post by salguod on 2006-10-08
I was able to install Perl-tk with "sudo apt-get install perl-tk"
douglas

---

### Post by salguod on 2006-10-09
ok, well now mapivi works but....
First, while playing with the options (preferences) I tried out several fonts because I find the default one to be rather ugly. one of the fonts I chose is worse than the original and i cannot change it back because the "apply" button has dissappeared!

Second, i can only use Mapivi when I open it as root in terminal. When I try to run it as my user it I get an error than It cannot create or access a file it needs.

These are the messages:
"Mapici would like to create a directory /home/douglas/.maprogs/mapivi in your home directory to store the configuration of MApivi and some button and background pictures"

I click "OK" then:
"Error making configdir /home/douglas/.maprogs/mapivi: Permission denied"
I click OK again, then the progam opens, but in the original form, without the reformated fonts. It seems to work Ok, but I cannot quit the program!

When I chose to quit, I get another error message:
"can't create /home/douglas/.maprogs/mapiviSearchDataBase: Permission denied at mapivi line 5696"

I click ok, the message goes away and the program stays open. 

The only way I can quit is to shut down the computer.

Is there any way to uninstall mapivi so I can reinstall it as user (i installed it as root)?

salguod

---

### Post by salguod on 2006-10-09
ok, I made progress. I blieve it is fully funcional now.

The issue I had was the "hidden" file called ".mapivi" in my home directory. I deleted it then ran mapivi again as user (not root), which made a new one.

Deleting it wasn't so simple though...
I had to go to into my home folder in terminal (konsole): cd /home/douglas/ 

to list "hidden" files in terminal, i used "ls -a"

to see their permissions, i used "ls -al"

i changed the .maprogs permissions with chmod: chmod a+rwx .maprogs

then i went to konqueror (i guess that would be nautilus for ubuntu), chose to "show hidden files" in the "view" menu, then moved it to the trash then smptied the trash.

that's it!

---

### Post by salguod on 2006-10-09
oops, the hidden file in the second sentence is called ".maprogs" not ".mapivi"
sorry for the confusion

---

### Post by Scunizi on 2007-04-09
I have an error in line 193 (use Image::Info qw(image_info dim); when running perl mapivi.  Since I'm running Dapper 6.06 I have not applied the patch listed above.  Is the patch related to  the error I'm getting?

---

### Post by Martin-Herrmann on 2007-04-16
Hi,

what kind of error do you get?
I would assume, that the Perl module Image::Info is missing.
You will find information about the Mapivi requirements (needed modules) here: [Mapivi Requirements]("http://mapivi.sourceforge.net/mapivi.shtml#requirements").

Regards
       Martin

---

### Post by austinderrick2 on 2007-05-09
Mapivi will not display thumbnails for me. I tryed to run it on Windows XP and the thumbnails did not show at all, and on Ubuntu all the thumbnails are the "EmptyThumbnail" image that is default with MapIVI.

Thanks,
Derrick

---

### Post by Martin-Herrmann on 2007-05-11
> **austinderrick2 said:**
> Mapivi will not display thumbnails for me. I tryed to run it on Windows XP and the thumbnails did not show at all, and on Ubuntu all the thumbnails are the "EmptyThumbnail" image that is default with MapIVI.


Is ImageMagick installed? Any error messages or warnings in the dos-box/shell where you started Mapivi?

Regards,
      Martin

---

### Post by daucourt on 2007-06-03
This may help users to install mapivi.
The following worked for me on Ubuntu 7.04 Feisty Fawn.
[FONT="Courier New"]
sudo aptitude install jpegpixi # interpolate dead pixels
sudo aptitude install libimage-exiftool-perl # exiftool EXIF/IPTC/XMP read/write
sudo aptitude install jhead # auto rotate
sudo aptitude install libjpeg-progs # jpegtran loss-less rotation
sudo perl -MCPAN -e 'install Image::MetaData::JPEG'
sudo perl -MCPAN -e 'install Image::Info'
sudo perl -MCPAN -e 'install Proc::ProcessTable'
mkdir -p ~/.maprogs/mapivi/trash
cp ~/mapivi091/pics/EmptyThumb.jpg ~/.maprogs/mapivi/EmptyThumb.jpg[/FONT]

Then enjoy program launching

[FONT="Courier New"]perl ~/mapivi091/mapivi[/FONT]

Thierry

---

### Post by Scunizi on 2007-06-03
Daucourt,  For someone that has "the first cup of Ubuntu" you've done a concise job of explaining how to get this to work.. Obviously, you've been around the block a little when it come to linux.  Thank you. :D

---

### Post by Scunizi on 2007-06-03
Sorry for the double post... I went through your instructions and found I was missing a couple of things namely ncftp and lynx.  It helps to have these installed before getting to the line {sudo perl -MCPAN -e 'install Image::MetaData::JPEG'} 

otherwise you'll have to install then manually type in where the program is located for that line to continue in its setup.  

Otherwise it worked like a champ!  Mapivi doen't have a real pretty interface but functional.  It also wants to create Thumbs files.  No biggie.  It's nice having a program that's fairly easy to add IPSC data to pics.  

Works on Dapper too.  :)

---

### Post by Scunizi on 2007-11-10
Followed the same instruction given for Feisty and worked fine on Gutsy. Yea! :)

---

### Post by bruceathome on 2008-05-03
Based on the replies by Daucourt and others the procedure I used to install mavipi in Hardy is as follows:


Download mavipi from: [http://mapivi.sourceforge.net/mapivi.shtml](http://mapivi.sourceforge.net/mapivi.shtml)

Then in a terminal:

sudo aptitude install jpegpixi

sudo aptitude install libimage-exiftool-perl

sudo aptitude install jhead

sudo aptitude install libjpeg-progs

sudo aptitude install ncftp

sudo aptitude install lynx

sudo aptitude install perl-tk

sudo perl -MCPAN -e 'install Image::MetaData::JPEG'

sudo perl -MCPAN -e 'install Image::Info'

sudo perl -MCPAN -e 'install Proc::ProcessTable'

mkdir -p ~/.maprogs/mapivi/trash

cp ~/mapivi097/pics/EmptyThumb.jpg ~/.maprogs/mapivi/EmptyThumb.jpg

Then enjoy program launching

perl ~/mapivi097/mapivi



Thanks for all the info people!

---

### Post by zmunson on 2008-05-13
I like these step-by-step instructions.  Thanks!  But I'm also enough of a linux newbie that I'm not sure what to do on step 1.  What file do I download from mapivi.  The .out file the page recommends?  Or the tar archive file listed as an 'alternate'?  Either way, what do I do/where do I put the file once I've got it?  

Thanks,

Z

---

### Post by daucourt on 2008-07-19
@zmunson, it looks that you need more help than the average ubuntu user, so do the following:

1. Open a terminal through menu Applications/Accessories/Terminal 
2. Then type the following commands

```
cd
wget http://heanet.dl.sourceforge.net/sourceforge/mapivi/mapivi097.tar.gz
tar xvfz mapivi097.tar.gz
```

3. then apply the full list of commands 

```
sudo aptitude install jpegpixi libimage-exiftool-perl jhead libjpeg-progs ncftp lynx perl-tk
sudo perl -MCPAN -e 'install Image::MetaData::JPEG'
sudo perl -MCPAN -e 'install Image::Info'
sudo perl -MCPAN -e 'install Proc::ProcessTable'
mkdir -p ~/.maprogs/mapivi/trash
cp ~/mapivi097/pics/EmptyThumb.jpg ~/.maprogs/mapivi/EmptyThumb.jpg
```

4. Then enjoy program launching

```
perl ~/mapivi097/mapivi
```

Thierry

---

