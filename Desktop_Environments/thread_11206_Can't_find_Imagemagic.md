---
title: "Can't find Imagemagic"
date: 2005-01-14
forum: Desktop Environments
---

### Post by CAPTAIN RON FL on 2005-01-14
I used Synaptic to get it. Now I can not find it. I thought it would be in graphics with gimp etc. Is there something else I am not doing?  :sad: 

Thanks, Ron

---

### Post by spartas on 2005-01-14
If I'm not mistaken, ImageMagic is an image manipulation library, not a full blown program.  It contains functions and scripts for image manipulation, and many people (like I) use it with online gallery programs.

---

### Post by duff on 2005-01-14
Go back to Synpatic and select imagemagick, then click the "Properties" button.  The "Installed Files" tab will show you the programs that were installed by the package.

---

### Post by CAPTAIN RON FL on 2005-01-14
I down loaded it to XP as a complete program off of the net. I know linux is not the same process as windows  but wouldn't  it download as a complete program??

I went back to Synpatic  and it showed a bunch of things down loaded.  Most of them are /usr/share/.

I still do not know how to find it to use it.

Thanks, Ron ](*,)

---

### Post by Yukonjack on 2005-01-14
Hello 

Have a look in /usr/bin for the executable it might be in there.

---

### Post by CAPTAIN RON FL on 2005-01-14
I looked in usr/bin/ but it was empty. Maybe I am not doing it right.  I looked in my filesystem  for usr then bin but I cold not find anything for it.





 Is there a How To to load programs anywhere? 

Thanks , Ron

---

### Post by Perfect Storm on 2005-01-14
There's a doc /usr/share/doc/imagemagick/index.html

<snip>
"ImageMagick is a robust collection of tools and libraries to read, write, and manipulate an image in many image formats including popular formats like TIFF, JPEG, PNG, PDF, PhotoCD, and GIF. With ImageMagick you can create images dynamically, making it suitable for Web applications. You can also resize, rotate, sharpen, color reduce, or add special effects to an image or image sequence and save your completed work in the same or differing image format. Image processing operations are available from the command line, as well as through C, C++, Perl, or Java programming interfaces."</snip>



.:=The AI Dude=:.

---

### Post by upmike on 2005-01-14
You might want to check your permissions. Also, imagemagick does not work like gimp - you need a frontend gui. By the way, I'm a dedicated Libranet user but am intrigued by the Ubuntu mission statement - so I'll hang around here awhile and see how you folks forum. Libranet, by the way, has a very nice family. I see it exists here too.

---

### Post by upmike on 2005-01-14
[QUOTE=CAPTAIN RON FL]I looked in usr/bin/ but it was empty. Maybe I am not doing it right.  I looked in my filesystem  for usr then bin but I cold not find anything for it.





 Is there a How To to load programs anywhere? 

Thanks , Ron[/QUOTE]


I'm assuming you mean applications ("programs"  is a windoze term)? And that you are trying to start them?  If you can't find it, try it (type the name of the application) from a  terminal command line or the "Run" feature.

---

### Post by CAPTAIN RON FL on 2005-01-14
I think this is way over my head. 

All I wanted was a way to resize my images so I could put them on ebay and my web page. :-( 

upmike : I do not know how to check  permissions.
              I do not know where to get  "you need a frontend gui" or what one is. I did google it and all I got was more confused. 8-[ 

AI :  I know how to open a terminal to use  command line. I just don't know what to put there.

OK so is there a program out there that I can down load and find  like gimp. Or maybe someone has a plug in for gimp that would let you easily resize the image.

Thanks, Ron

---

### Post by ape on 2005-01-15
The following "program" files are installed by the imagemagick package:

/usr/bin/compare
/usr/bin/composite
/usr/bin/conjure
/usr/bin/convert
/usr/bin/identify
/usr/bin/mogrify
/usr/bin/montage
/usr/bin/animate
/usr/bin/display
/usr/bin/import

You would use /usr/bin/display <filename> to show a graphics image.  You are probably wanting to use the convert program to manipulate your images.  You can type 'man convert' for information on how to use the file.

The reason that it doesn't automatically show up in the Gnome Menus is that imagemagick supplies only command line utilties, which by default do not make it into the menus.

---

### Post by Perfect Storm on 2005-01-15
[QUOTE=CAPTAIN RON FL]I think this is way over my head. 

All I wanted was a way to resize my images so I could put them on ebay and my web page. :-( 

upmike : I do not know how to check  permissions.
              I do not know where to get  "you need a frontend gui" or what one is. I did google it and all I got was more confused. 8-[ 

AI :  I know how to open a terminal to use  command line. I just don't know what to put there.

OK so is there a program out there that I can down load and find  like gimp. Or maybe someone has a plug in for gimp that would let you easily resize the image.

Thanks, Ron[/QUOTE]

Try the program Xnview. It's not in the rep. You have to add the program manually.

It's very easy to resize in gimp. Gimp is as powerful as Photoshop, you just need to learn how it work. To resize: 

Open gimp
Open the picture you want to resize
Choose 'Image' in the tab
and then choose 'Scale Image'. Voila! Very easy.


=:.The AI Dude=:.

---

### Post by CAPTAIN RON FL on 2005-01-15
AI:  

Gimp worked.  =D>  :D 

Just did not know where to look.

I am going to go to the library And see if they have a book on it.

I would like to try the program Xnview. I google it and it looks good.  I checked the HOW TO"S and could not find one on doing a manual install. I am searching now on ubuntu forms.  Can you help me with this?

APE: 

Thanks .  I tried that too. It's just to much to go through.

I should add that I am very new at this.

Thanks, Ron

---

### Post by HankB on 2005-01-16
Gimp is a great program and if you want to work with images, I highly recommend it. But some times you want to do something from the command line and ImageMagick provides those capabilities. I'm surprised that no one has pointed you to the ImageMagick web page at [http://www.imagemagick.org/](http://www.imagemagick.org/). Click on "Command-line programs" and you'll see all of the programs that were installed on your system (if Imagemagick was installed."

HTH,
hank

---

### Post by CAPTAIN RON FL on 2005-01-16
Thanks Hank,

I just went there and checked it out.  I read some of the stuff earlier... just the things for windows. I down loaded it in XP so I thought it woul be the same for linux.

I am now trying to to get XnView install. 


This has really been a learning process for me. I thought that windows was a pain... well it is. I guess this is not so bad.  Just a little hard for someone in there 50's to cram in their pea brain.

Thanks, Ron

---

### Post by Perfect Storm on 2005-01-16
Okay, here's how you install Xnview.

website: [http://www.xnview.com/](http://www.xnview.com/)

Grab the file called(linux x86): XnView v1.68.1 (static) + NView/NConvert v4.16
But choose the rpm version and download it.

Now open the terminal

cd /to/where/you/saved/the/file
sudo alien XnView-static.i386.rpm (alien is a program that convert packages and is installed default on your OS)
sudo dpkg -i xnview_1.68-2_i386.deb (dpkg -i installs X.deb package)

Now you can write xnview in the terminal to start the program.

You want the program in the 'Application' tab?

write in the terminal:
nautilus applications:///Graphics

A window pop up

Then choose the file tab --->  Create Launcher

**Name:** Xnview
**Command:** xnview

If you have an icon for it you can also fill that out.

---

### Post by CAPTAIN RON FL on 2005-01-16
AI, 

    Thanks. Everything work ok to use it with terminal. I made an icon for it and put it in graphics. That worked too.  :D 

THANK YOU !!!! THANK YOU!!!!  :D  

That was fairly easy and painless. I was wondering why I was able to do it with rpm and not tarball?

rpm seem quicker or at least less steps anyway.

Thanks again :D  I have lots to play with now. I got qftp so I can upload to my web
 
site and XnView to do the pictures. Now all I have to do is learn how to use them. I

 am off to play now :D 

Ron

---

### Post by Perfect Storm on 2005-01-16
That might be a way to solve the tarball, but nxview tarball is relying on an 'su' and ubuntu you're using 'sudo' root command. So the painless and non-complicated way was to convert the .rpm file into a .deb file and you can easely uninstall again.


.:=The AI Dude=:.

---

### Post by Yukonjack on 2005-01-16
AI
Good to know about the rpm conversion to deb, is there anyway to make su root work in Ubuntu? I never quit learning with gnu/linux, one of the reason why I love it. :)
Thanks AI

---

### Post by orlando_nick on 2005-07-25
[QUOTE=ape]The following "program" files are installed by the imagemagick package:

/usr/bin/compare
/usr/bin/composite
/usr/bin/conjure
/usr/bin/convert
/usr/bin/identify
/usr/bin/mogrify
/usr/bin/montage
/usr/bin/animate
/usr/bin/display
/usr/bin/import

You would use /usr/bin/display <filename> to show a graphics image.  You are probably wanting to use the convert program to manipulate your images.  You can type 'man convert' for information on how to use the file.

The reason that it doesn't automatically show up in the Gnome Menus is that imagemagick supplies only command line utilties, which by default do not make it into the menus.[/QUOTE]

Just wanted to mention how much this helped! Have been trying to get Coppermine Gallery running for a few days now. Couldnt figure out the path to the ImageMagick 'convert' command. 

Actually installed Fedora Core 4, then CentOS 4, had a number of config problems, and came back to Ubuntu. Seems like I'll be sticking with it  ;-) 
Thanks!

---

