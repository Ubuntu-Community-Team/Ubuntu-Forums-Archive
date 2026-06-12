---
title: "Anyone got BibleTime working?"
date: 2005-01-10
forum: Desktop Environments
---

### Post by jonny on 2005-01-10
I've successfully installed some other KDE apps, but BibleTime just segfaults and dies on startup.  I know it's from the unsupported universe, but I'd really like to get this going.

Has anyone else succeeded?

---

### Post by brk3 on 2005-01-12
There's a bible study app for gnome that seems really good(I havent it tried yet because my access to my pc is limited at the moment!  :cry: )

It does seem great though, heres the url: 
[http://www.gnomefiles.org/app.php?soft_id=23](http://www.gnomefiles.org/app.php?soft_id=23)

---

### Post by jonny on 2005-01-12
Thanks.  I'll give it a try - it looks great.  I'm beginning to realise that, although the ubuntu repositories are huge, they just scratch the surface of the free software that's out there.

---

### Post by jonny on 2005-01-16
The problem appears to be in the Sword libraries (both BibleTime and  GnomeSword depend on these).  I've tried downloading a fresh Sword tarball from their site and recompiling everything, but get the same failure.  I've a few more options to fiddle with, but, if I don't succeed, I'll raise the problem in the Sword forums.

---

### Post by brk3 on 2005-01-20
"Thanks. I'll give it a try - it looks great. I'm beginning to realise that, although the ubuntu repositories are huge, they just scratch the surface of the free software that's out there."  - Thats very true  8) 

Maybe you could try posting the error your getting when trying to install/compile?

---

### Post by Hikaru79 on 2005-01-20
Just for the record, I don't think it's a repository problem -- BibleTime is working fine over here. Then again, I'm in Hoary...

---

### Post by jonny on 2005-01-20
Success!  I'm looking at GnomeSword and downloading various versions of the Bible as I type.  For all you ubuntu-loving Christians, this post describes how I did it.  Note that these instructions assume a degree of familiarity with ubuntu; if you have difficulty following them, post a question to the forum and I'll try to help. 

1. Create a working directory for the compilations.  I used:

  /home/jonny/Downloads/gnomesword

but you can use whatever you like.  Just change the scripts that follow accordingly.

2. Download the file sword-1.5.7a.tar.gz and copy it into that directory.  You can find it [here](http://www.crosswire.org/sword/software/swordapi.jsp) (click on the link marked Current Version.  If the version number has changed by the time you read this, you'll have to change every reference to the files and directories in the scripts below)

3. Download the file gnomesword-2.1.1.tar.gz and copy it into the same directory.  You can find it [here](http://gnomesword.sourceforge.net/download.html) (I used the latest unstable tarball and I repeat the version number caveat)

4. Open the /home/jonny/Downloads/gnomesword in File Manager, right-click on each of the downloaded files and select 'Extract Here'

5. Open Synaptic Package Manager, and install the following packages:
  libgtkhtml3.2-dev
  gtkhtml3.2
  libgtk2.0-dev
  
(I have a really bad feeling about the completeness of this package list, as I've compiled lots of other programs before GnomeSword and don't know for certain which ones are needed.  Perhaps someone else can help me out)

6. Open a terminal session and enter the following series of commands
```
$ cd /home/jonny/Downloads/gnomesword/sword-1.5.7a
$ ./usrinst.sh
$ make
$ sudo make install
$ sudo make install_config
```Note that this isn't the usual set of commands for compiling a program.  The standard ./configure... make... make install routine will fail.

As the text flashes past, do look out for strange error messages.  They're probably an indication that you don't have all the prerequisite packages installed; if I've missed any out, please post them to this thread.

7. That should have installed the Sword libraries.  You can check things are working OK so far by typing

 ```
$ ./testlib
```All being well, you'll be rewarded with a bible reference but, as yet, you'll have no supporting text

8. Now you need to compile GnomeSword itself.  Use these commands:

```
$ cd /home/jonny/Downloads/gnomesword
$ ./configure
$ make
$ sudo make install
```
9. Check that things have worked with this command

```
$ gnomesword2
```All being well, you'll see a startup wizard.  I accepted all the default options.

10. Now you need to get some Bible texts.  Connect to the internet (if you're on dial-up), choose Edit > Module Manager and in Configure select the Remote radio button. Now click on Install, and choose your favourite Bibles, commentries and the like.  Hit install, and you're away.

11. Finally, you need a launcher.  Gnomesword doesn't put an icon in ubuntu's icons directory, so copy one there for convenience:
 ```
$ sudo cp /home/jonny/Downloads/gnomesword/gnomesword-2.1.1/pixmaps/gs2-48x48.png /usr/share/pixmaps/gs2-48x48.png
```Now view a suitable submenu off ubuntu's Applications menu, right-click and choose Entire Menu > Add new item to this menu.  In the dialogue box, choose a suitable name and comment, and enter gnomesword2 in the Command box.  Click on the Icon button, and choose gs2-48x48.png from the list.

Lengthy, but worth it.  If you love the Bible, you'll love this application  :D.  But if you really can't get it cracked, wait for the Hoary distribution and install BibleTime instead.

---

### Post by fradek on 2005-03-04
> **jonny]Success!  I'm looking at GnomeSword and downloading various versions of the Bible as I type.  For all you ubuntu-loving Christians, this post describes how I did it.  Note that these instructions assume a degree of familiarity with ubuntu said:**
> here[/URL] (click on the link marked Current Version.  If the version number has changed by the time you read this, you'll have to change every reference to the files and directories in the scripts below)

3. Download the file gnomesword-2.1.1.tar.gz and copy it into the same directory.  You can find it [here](http://gnomesword.sourceforge.net/download.html) (I used the latest unstable tarball and I repeat the version number caveat)

4. Open the /home/jonny/Downloads/gnomesword in File Manager, right-click on each of the downloaded files and select 'Extract Here'

5. Open Synaptic Package Manager, and install the following packages:
  libgtkhtml3.2-dev
  gtkhtml3.2
  libgtk2.0-dev
  
(I have a really bad feeling about the completeness of this package list, as I've compiled lots of other programs before GnomeSword and don't know for certain which ones are needed.  Perhaps someone else can help me out)

6. Open a terminal session and enter the following series of commands
```
$ cd /home/jonny/Downloads/gnomesword/sword-1.5.7a
$ ./usrinst.sh
$ make
$ sudo make install
$ sudo make install_config
```Note that this isn't the usual set of commands for compiling a program.  The standard ./configure... make... make install routine will fail.

As the text flashes past, do look out for strange error messages.  They're probably an indication that you don't have all the prerequisite packages installed; if I've missed any out, please post them to this thread.

7. That should have installed the Sword libraries.  You can check things are working OK so far by typing

 ```
$ ./testlib
```All being well, you'll be rewarded with a bible reference but, as yet, you'll have no supporting text

8. Now you need to compile GnomeSword itself.  Use these commands:

```
$ cd /home/jonny/Downloads/gnomesword
$ ./configure
$ make
$ sudo make install
```
9. Check that things have worked with this command

```
$ gnomesword2
```All being well, you'll see a startup wizard.  I accepted all the default options.

10. Now you need to get some Bible texts.  Connect to the internet (if you're on dial-up), choose Edit > Module Manager and in Configure select the Remote radio button. Now click on Install, and choose your favourite Bibles, commentries and the like.  Hit install, and you're away.

11. Finally, you need a launcher.  Gnomesword doesn't put an icon in ubuntu's icons directory, so copy one there for convenience:
 ```
$ sudo cp /home/jonny/Downloads/gnomesword/gnomesword-2.1.1/pixmaps/gs2-48x48.png /usr/share/pixmaps/gs2-48x48.png
```Now view a suitable submenu off ubuntu's Applications menu, right-click and choose Entire Menu > Add new item to this menu.  In the dialogue box, choose a suitable name and comment, and enter gnomesword2 in the Command box.  Click on the Icon button, and choose gs2-48x48.png from the list.

Lengthy, but worth it.  If you love the Bible, you'll love this application  :D.  But if you really can't get it cracked, wait for the Hoary distribution and install BibleTime instead.

Thank you! I love Sword, had it operating on my Mandrake, Fedora and SuSE, recently switched to Ubuntu and missed the Bibletime a lot...

If you speak Polish there are additional modules available - Biblia Warszawsko-Praska and Biblia Gdanska as well as Psalms by Kochanowski if I remember correctly - check the [www.sword.strona.pl](www.sword.strona.pl) to learn more. Radek F., Poland, EU (yes, my country stopped software patents in the EU! :D)

---

### Post by jonny on 2005-03-09
Just been setting up another PC.  Hoary actually has gnomesword in the universe, so you can install it through Synaptic package manager.  And the Sword libraries work this time, too.

Ubuntu just gets better and better!

---

### Post by Xian on 2005-03-09
[QUOTE=jonny]Just been setting up another PC.  Hoary actually has gnomesword in the universe, so you can install it through Synaptic package manager.  And the Sword libraries work this time, too.[/QUOTE]
Hey, that's sweet. I hadn't noticed that yet in Hoary. :)

---

### Post by libertyforever on 2005-10-20
Newbie here.  I have downloaded gnomesword and have nothing working in it (MHCC, Nave's, different versions, etc.).  Went to Synaptic and downloaded all the modules I could see that were part of gnomesword, (libsword4, libsword-dev, sword-comm-mhcc, sword-comm-pers, sword-dict-naves, sword-text-web, bible-kjv, bible-kjv-text, perspic-texts) but still nothing there when I open gnomesword.  I saw another thread _[here]("http://www.ubuntuforums.org/showthread.php?t=55843&highlight=gnomesword+modules")_ that said to download gcc, ccp, and c++, but I appear to already have those too.  How do I get gnomesword to recognize these modules?  I'm running Hoary.  Thanks for being there!

---

### Post by matthew on 2005-10-20
In the version of GnomeSword I am using (I have Breezy and got it from the Repos...it's version 2.1.2) I can add modules this way.

Edit->Module Manager

Configure->Remote->crosswire

Drop down to Install in the left hand frame, choose away and click the install button.

Worked for me. [Screenshot here.]("http://ubuntuforums.org/gallery/showimage.php?i=1150&catid=newimages") (Look at the lower left quadrant.)

---

### Post by libertyforever on 2005-10-20
Thanks Matthew.  I have version 2.0.0  My edit menu only has [COLOR="Blue"]Copy, Search, Advanced Search,[/COLOR] and [COLOR="Blue"]Prefences.[/COLOR]  Do you know if there are repos I can access to upgrade to version 2.1.2 in Hoary?:confused:

---

### Post by matthew on 2005-10-20
Well, you could upgrade to Breezy, but that is going to be more work. Here's another option.

Let me think...about 6 months ago I installed GnomeSword in Hoary and added multiple modules that I had downloaded from the web site just like you have done so I know it is possible. I just need to try to shake out the cobwebs and see if I can remember how I did it. Without a Hoary installation available for me to look at I will have to take some guesses.

I seem to recall reading something on the Sword Project web site at [http://www.crosswire.org/sword/index.jsp](http://www.crosswire.org/sword/index.jsp) on how to install modules. Let me see if I can find it.

Here it is:

[LIST]
**Raw**: Find the directory where your sword modules are installed.  This directory will contain subdirectories: mods.d and modules.  Some possibilities include \Program Files\CrossWire\The SWORD Project, or /usr/share/sword. Unzip the module to this directory.  The module zip file will unzip to populate the mods.d and modules subdirectories. [/LIST] From this page: [http://www.crosswire.org/sword/modules/moduleinstall.jsp](http://www.crosswire.org/sword/modules/moduleinstall.jsp)

So, look on your computer for the location of the current modules. /usr/share/sword seems the most likely place.

Here is how you transfer the compressed files you downloaded to that directory and unzip them. I will assume you downloaded them to /home/liberty. Do this for each module you downloaded. Make sure GnomeSword is closed while you are doing this.

Open a terminal from Applications->Accessories->Terminal and type
```
sudo mv /home/liberty/module.zip /usr/share/sword/module.zip
sudo unzip /usr/share/sword/module.zip
```

That should do it. Open GnomeSword and they should be there.

---

### Post by libertyforever on 2005-10-20
Thanks Matthew!  It worked - at least all the stuff is there.  Now, the learning curve on how to use it . . ..:rolleyes: 

It seems like it would have been easier to use gnome file roller to do this, but I don't know what Extract File and Add File means, along with all the other options.  So, I just used the shell like you suggested, which is pretty new to me, but waded my way through it.  Anyway, thanks for the help.  Do you know of a tutorial to learn how to use gnomesword?  If not, I guess it's learn as I go!

---

### Post by matthew on 2005-10-20
[quote=libertyforever]Thanks Matthew! It worked - at least all the stuff is there. Now, the learning curve on how to use it . . ..:rolleyes: 

It seems like it would have been easier to use gnome file roller to do this, but I don't know what Extract File and Add File means, along with all the other options. So, I just used the shell like you suggested, which is pretty new to me, but waded my way through it. Anyway, thanks for the help. Do you know of a tutorial to learn how to use gnomesword? If not, I guess it's learn as I go![/quote] Great! I'm glad we got it working for you!

The reason I chose to give shell commands is because it is easier than describing "now click on the ..." Also, as you get more accustomed to it you will find that using the command line is a lot faster for most things. The learning curve is admittedly steep at the beginning, though.

I haven't seen a tutorial for gnomesword. What I know I have learned by clicking everything at least once to see what it does.

Have fun!

---

### Post by skoal on 2005-10-21
It seems like you guys got this one figured out, and I noticed this thread is on 'ole faithful Warty.  So, I thought I'd mention I ran across this thread: [http://www.ubuntuforums.org/showthread.php?t=2163&highlight=bibletime](http://www.ubuntuforums.org/showthread.php?t=2163&highlight=bibletime)

...which basically had the same problem.  If you're running warty you probably could have just found a newer libsword library from debian or from the hoary repos, download it, and then install it with dpkg -i.

...

I'm running breezy and kde, but just one (unrelated) question on BibleTime: How the frankincense and myrrh do I use the "Magnify" feature? I couldn't seem to get an answer to that from their FAQ. It just shows a blank box no matter what I do.  Big bold letters for my weak feeble eyes sure would be dandy!

much obliged.

\\//_

---

### Post by matthew on 2005-10-21
[quote=skoal]It seems like you guys got this one figured out, and I noticed this thread is on 'ole faithful Warty. So, I thought I'd mention I ran across this thread: [http://www.ubuntuforums.org/showthread.php?t=2163&highlight=bibletime]("http://www.ubuntuforums.org/showthread.php?t=2163&highlight=bibletime")

...which basically had the same problem. If you're running warty you probably could have just found a newer libsword library from debian or from the hoary repos, download it, and then install it with dpkg -i.

...

I'm running breezy and kde, but just one (unrelated) question on BibleTime: How the frankincense and myrrh do I use the "Magnify" feature? I couldn't seem to get an answer to that from their FAQ. It just shows a blank box no matter what I do. Big bold letters for my weak feeble eyes sure would be dandy!

much obliged.

\\//_[/quote]

Hey, skoal. libertyforever is running Hoary and I am running Breezy and we both are using Gnomesword on Gnome. Maybe someone else who is using Bibletime on KDE will jump in here...just wanted you to know someone saw your post. :)

---

