---
title: "Uninstall wine tools and wine"
date: 2006-07-24
forum: Desktop Environments
---

### Post by jrjr on 2006-07-24
I installed wine with Synaptic and then installed wine tools. Internet explorer and OE were installed by default... I guess, but they never worked right. IE would open as a blank window with no tool bars... completely blank. I tried office 2000 install but that didnt work either. Maybe its me LOL.
In any event, I want to completely uninstall and start over. I uninstalled IE, OE, and office with wine tools but there are still folders in .wine/c/program files that are quite full... looks like the programs are intact. 

1. Why werent they removed? 
2. Can I simply delete the folders? 

I can uninstall wine with Synaptic but what about wine tools? I see in the winetools-0.9jo-III folder there is an uninstaller. 

3.Should I use that uninstaller to remove wine tools?

---

### Post by jrjr on 2006-07-24
Please dont let this be another disapearing question

---

### Post by jrjr on 2006-07-24
Nobody knows how to uninstall programs?

---

### Post by elwood_j_blues on 2006-07-24
Well you can uninstall programs on Ubuntu using

sudo apt-get remove packagename


(on a console)

Just search the forum for more information; I am sure a few thousand people already asked this. Have fun!

---

### Post by jrjr on 2006-07-24
Thanks for that tip. I didn't know it but I made a note of it.
Unfortunately it doesnt really answer any of my questions from the first post. 

Anybody else?

---

### Post by exif on 2006-07-24
The files in .wine/c are all wine-only files (they aren't required by anything but win apps and wine) so it's prefectly safe to remove them manually. When re-installing wine and wine-tools the files that are required will be installed.

---

### Post by jrjr on 2006-07-24
> **elwood_j_blues said:**
> Well you can uninstall programs on Ubuntu using

sudo apt-get remove packagename



So, I used this to get wine tools:

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz
```

Would I use this to remove it then: ?

```
sudo apt-get remove winetools-0.9jo-III.tar.gz
```

---

### Post by jrjr on 2006-07-24
.bmp

---

### Post by ColinG on 2006-07-24
There is no harm in trying: sudu apt-get remove "package name" and it was recommended earlier in this thread.

---

### Post by jrjr on 2006-07-24
Yep, in post #7 that was my exact question. Is my syntax correct?

---

### Post by jrjr on 2006-07-24
.

---

### Post by jrjr on 2006-07-24
I ran this and got the result below it. All the things are still in the winetools folder.
```
sudo apt-get remove winetools-0.9jo-III.tar.gz
```

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package winetools-0.9jo-III.tar.gz

---

### Post by elwood_j_blues on 2006-07-24
> **jrjr said:**
> ```
sudo apt-get remove winetools-0.9jo-III.tar.gz
```

No, you can only uninstall software with apt that you already installed with apt in the first place.

When you install stuff from the source like you apparently did, there is no general way of uninstalling, unless the respective package provides you with one.

Why did you do that?

I recommend you try installing wine and winetools with apt to begin with. Then chances are, it will work on Ubuntu.

Did you read the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Applications_in_Linux_.28Wine.29")?

---

### Post by ColinG on 2006-07-25
The syntax is wrong anyway. Should be - sudo apt-get remove winetools.

tar.gz is the downloaded installation files that can just be  deleted.

---

### Post by KaeseEs on 2006-07-25
Check your .wine directory; installations from source (what you did) often come with an uninstall script, often called 'uninst.sh', 'uninstall', or something similar.  Either way, your best bet for installing software in Ubuntu is:

```
sudo aptitude install *packagename*
```

To remove anything installed this way, use:

```
sudo aptitude remove *packagename*
```

If you don't know the name of the package you want to install, use:

```
aptitude search *keyword*
```

Better yet, thiss can all be done from a graphical interface, using:

```
gksudo synaptic
```


While this may not be a solution to your current problem, I hope it'll be helpful in the future.

---

### Post by jrjr on 2006-07-25
> **KaeseEs said:**
> Check your .wine directory; installations from source (what you did) often come with an uninstall script, often called 'uninst.sh', 'uninstall', or something similar.  Either way, your best bet for installing software in Ubuntu is:

```
sudo aptitude install *packagename*
```

To remove anything installed this way, use:

```
sudo aptitude remove *packagename*
```


If you don't know the name of the package you want to install, use:

```
aptitude search *keyword*
```

Better yet, thiss can all be done from a graphical interface, using:

```
gksudo synaptic
```


While this may not be a solution to your current problem, I hope it'll be helpful in the future.

Well... an answer to the original questions -
Thanks for that... i'm learning :) 




elwood -

> **elwood_j_blues said:**
> No, you can only uninstall software with apt that you already installed with apt in the first place.

When you install stuff from the source like you apparently did, there is no general way of uninstalling, unless the respective package provides you with one.

Why did you do that?

I recommend you try installing wine and winetools with apt to begin with. Then chances are, it will work on Ubuntu.

Did you read the [Ubuntu Guide]("http://ubuntuguide.org/wiki/Dapper#How_to_install_Windows_Applications_in_Linux_.28Wine.29")?

Why did I do this?
Because in post #4 of this thread  you said this:

> **elwood_j_blues said:**
> 
Well you can uninstall programs on Ubuntu using
sudo apt-get remove packagename


> **elwood_j_blues said:**
> 

When you install stuff from the source like you apparently did, there is no general way of uninstalling, unless the respective package provides you with one.



So there is no way to uninstall wine tools in this case... is that what you are saying?

---

### Post by jrjr on 2006-07-25
So I thought to myself, self - maybe we should just leave winetools here, take out wine, reinstall wine, and reinstall winetools right over the top. Ok, good thought self.

I had installed wine with Synaptic. I opened Synaptic and marked wine for complete removal. The process completed, or so the prompt said, and I closed the app.

Checking my directory, the wine folder is still there with what seems to be all the program info in it. 

I'm not really hoping for a complete answer from anyone, I guess its more of a rant. Its looking like time to give Ubuntu the boot and try something else but that will probably mean the end of linux for me and just go back to windows. I expect the other flavors of Linux to be unfriendly as well.  

This is ridiculous. There are at least 4 ways to install something and probably more once I learn about them. When you ask for help you get bits and pieces of conflicting info from different people. On occasion somebody will say to do something and then ask you "why did you do that?"

Some of the ways to install cannot be reversed so that you can't remove the programs, and the ways that are supposed to be so easy to uninstall? Well they just dont work. What a crock that is.

I struggled for 5 days to get my video working correctly and gave up. Posts here get no answers and I have nowhere else to turn. 

So I really have nowhere to turn. There is no definitave source of info for a newbie that doesnt speak the linux lingo. Its a very, very tough transition and not one that I am sure I am willing to make. 

I have numerous certifications in windows so its not like im completely uninformed when it comes to computers, just linux. 

I remember back in early DOS days I had actual people to talk to in person that were willing to help. There is nobody around here that I know of that uses Linux so I am basically floating in my own boat at sea with no land in sight. 

Maybe another version will be better...

I really think that Ubuntu should seriously consider about how they are representing this product as being user friendly.... its not

---

### Post by elwood_j_blues on 2006-07-25
Sorry, but what you are saying is not true. The information is not at all conflicting. Let's summarize what we told you.

a) you installed Wine from a generic download, called ...tar.gz, that makes it generally harder to configure and especially uninstall software when there is a package you could install instead. Mistakes happen. No problem, this is why we tried to show you how to do it correctly the next time.
b) a package (we didn't tell you, sorry) is a piece of software precompiled for the individual distribution you are using. Packages can be installed using the package manager of you distribution. For Ubuntu, this is "apt". KaeseEs gave you the essence of how it is used.
c) you were asked to look for an uninstall script in the .wine folder. If there is none, delete it from your home folder and install the actual Ubuntu package for this software.
d) reading is absolutely essential for success. Not reading a single line and saying afterwards that Linux is "unfriendly" does not help succeeding. In this regard, I already pointed you to the [UbuntuGuide]("http://ubuntuguide.org/wiki/Dapper"), which is a good starting point.
e) if you are not firm using the console yet, try to start off with the GUI frontends that are there to help you. You apparently jumped right into the console, messed something up a little, got frustrated and are about to drop the whole thing. This is like pulling a few plugs under the hood of your new Mercedes and ranting afterwards that you don't know where to put the plugs. Start driving first and see how it feels. Again, in this respect, KaeseEs already pointed you to a good piece of software called synaptic which is a frontend to apt-get and should help you to install packages without any significant hassle.

You see, people were helping you, they were supportive, and instead of randomly ranting you could have tried to understand them and ask any additional questions that you might come up with. But insulting people is generally a very bad idea if you want them to help you.

---

### Post by dpm on 2006-07-25
> **jrjr said:**
> So, I used this to get wine tools:

```
wget http://ds80-237-203-29.dedicated.hosteurope.de/wt/winetools-0.9jo-III.tar.gz
``` 
Would I use this to remove it then: ?

```
sudo apt-get remove winetools-0.9jo-III.tar.gz
```

No.

'*apt-get remove*', i.e. the '*apt*' tool [1] is a console-based application that can be used to install, uninstall and generally manage **packages**. In Ubuntu, this can also be done with 'Synaptic', which is simply a graphical frontend to 'apt', with nearly the same functionality.

There are basically two ways of installing software in Linux:[LIST]
[*]**_From source_**: you download the sources of the application, usually in the form of a tarball (file with a .tar.gz or .tar.bz2 extension, which contains the compressed sources). You then uncompress them, compilethem and install them. Advantages: you can always get the latest version of an application. Disadvantages: there is no guarantee that the application will compile on your system or that it won't break something else, the application can take a long time to compile, etc. Furthermore, there is no easy way to control which files/applications you install.[/LIST][LIST]
[*]**_From packages_**: that's the way Ubuntu and most other distro work (although you can still compile from source). The people who design and maintain Ubuntu make official repositories available, which contain packages for each application you want to install. These packages have been created are guaranteed to work for Ubuntu, and can be easily installed/uninstalled with the use of special tools (e.g. Synaptic, apt, or aptitude, to name a few). Ubuntu is a distro based on Debian[2], and it used debian packages, which have a .deb extension. Advantages: the packages are easy and quick to install/uninstall, they will work for your current distro and they have been thoroughly tested for Ubuntu. The package manager takes care of any other applications which need to be installed for your application to run. Disadvantages: you don't get the latest, bleeding-edge versions of applications from the repositories until they have been thoroughly tested, which basically means until the next release cycle.[/LIST]What you downloaded is a compressed file (called tarball) which contains the sources of the application, which you probably compiled with something similar to './configure' and installed with 'sudo make install'. So you **were installing from source and you cannot uninstall the application with 'sudo apt-get remove'.**

In order to uninstall this application, open a terminal window, change the directory to the one where you uncompressed and compiled the sources and type:
```
sudo make uninstall
``` 

Please let us know how you installed the application in the first place so I or anyone else can give you further assistance.

[1] type 'man apt' on the terminal to get to know more about the 'apt' tool through its man page.
[2]www.debian.org

---

### Post by dpm on 2006-07-25
Hmm...

Somehow I managed to miss the second page of the thread. Now that I'm reading it, I see the question was already answered, so sorry for the duplicate information.

Cheers.

---

### Post by jrjr on 2006-07-25
> **elwood_j_blues said:**
> Sorry, but what you are saying is not true. The information is not at all conflicting. Let's summarize what we told you.

What is not true with what I am saying? You have no idea what i've been through, done and not done, and unless you do you should not make statements like that. For  instance I installed wine with help from this page which says to use wget:

[http://www.ubuntuforums.org/showthread.php?t=149585&highlight=install+wine](http://www.ubuntuforums.org/showthread.php?t=149585&highlight=install+wine)

Now this information is contained on THIS forum's pages and is in conflict with info that I received in this thread. 


> **elwood_j_blues said:**
> 
a) you installed Wine from a generic download, called ...tar.gz, that makes it generally harder to configure and especially uninstall software when there is a package you could install instead. Mistakes happen. No problem, this is why we tried to show you how to do it correctly the next time.

I installed WINE TOOLS from the tar.gz. If you would READ what I write, in the very first post of this thread. and in other places I stated that I installed wine with Synaptic and using Synaptic to uninstall it did not work. There is a lot of this going on here... people responding without reading and understanding fully. It makes for a lot more steps than is necessary in troubleshooting. Read Read Read  



> **elwood_j_blues said:**
> 
b) a package (we didn't tell you, sorry) is a piece of software precompiled for the individual distribution you are using. Packages can be installed using the package manager of you distribution. For Ubuntu, this is "apt". KaeseEs gave you the essence of how it is used.

See above

> **elwood_j_blues said:**
> 
c) you were asked to look for an uninstall script in the .wine folder. If there is none, delete it from your home folder and install the actual Ubuntu package for this software.
 
Before this suggestion was offered I had posted that same fact. I asked if I should use the uninstall file and nobody bothered to read what I wrote. Its all here in this thread... read read read


> **elwood_j_blues said:**
> 
d) reading is absolutely essential for success. Not reading a single line and saying afterwards that Linux is "unfriendly" does not help succeeding. In this regard, I already pointed you to the [UbuntuGuide]("http://ubuntuguide.org/wiki/Dapper"), which is a good starting point.

bite me - practice what you preach. You contradicted yourself here... you should read this thread sometime whey you are not busy either giving misinformation or condemning someone.

> **elwood_j_blues said:**
> 
e) if you are not firm using the console yet, try to start off with the GUI frontends that are there to help you. You apparently jumped right into the console, messed something up a little, got frustrated and are about to drop the whole thing. This is like pulling a few plugs under the hood of your new Mercedes and ranting afterwards that you don't know where to put the plugs. Start driving first and see how it feels. Again, in this respect, KaeseEs already pointed you to a good piece of software called synaptic which is a frontend to apt-get and should help you to install packages without any significant hassle.

see above

> **elwood_j_blues said:**
> 
You see, people were helping you, they were supportive, and instead of randomly ranting you could have tried to understand them and ask any additional questions that you might come up with. But insulting people is generally a very bad idea if you want them to help you.

I wasn't trying to insult anyone before in this thread but you can consider yourself officially insulted now. Before offering advice you should make sure that what you are saying is credible.

Edit - I am not sure what I will do here but I do know one thing Elwood, please stay out of my threads from now on.

---

### Post by elwood_j_blues on 2006-07-25
Fair enough. It does not seem like you were willing to learn anything in the first place anyway.

---

### Post by fhmanas on 2006-08-03
jrjr, I got what you were asking from your post, and is exactly what happened to me.  I am a newbie as well and exploring Ubuntu and Linux. I got IE to work but it suddenly stopped. Don't give up as well.

I did also install internet explorer from the same post the you followed. It actually works until you update Wine, however like the original poster said IE is somehow broken in the newer version of Wine.  So do it again but stop up to the point at the update portion, meaning don't update to the latest yet.  Try it first.

To uninstall Wine -> sudo apt-get remove wine

-check that it has been removed, by executing wine, it should not find it.
-this should remove '~/.wine' and subdirectories, but if it did not, i pretty much guess that it would be safe to remove the directory and everything underneath it, since in all essense the the only thing using it is Wine.

To uninstall Winetools (you're version) 
   -> Do a 'sudo ./uninstall' at the winetools-0.90-III directory or the install directory

   -> This will probably leave your winetools directory intact, I just removed it using 'rm -r winetools', note I did not use sudo since it was localized to my user.


To the other posters, be patient with Ubuntu newbies like us.  No point in being rude and cryptic, it's counter-productive. 

NOTE: Please don't take the last line as being disrespectful

---

### Post by aborup on 2008-02-22
Thank you FHManas!
I'm a newbie and your post, at the end of this long and sometimes bitter thread, helped me with this exact same problem.

Your to-the-point recipe for removal was on target.

Thanks again!

Big Al

---

