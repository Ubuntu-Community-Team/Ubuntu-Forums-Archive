---
title: "HOW TO: Install Kiba-Dock"
date: 2007-09-18
forum: Desktop Effects &amp; Customization
---

### Post by mattgaunt on 2007-09-18
[SIZE="4"]**[COLOR="Red"][CENTER]******** This How-To Works With Gutsy Gibbon, Feisty Fawn and Hardy Heron ********[/CENTER][/COLOR]**
[/SIZE]

[SIZE="4"]**[CENTER]******** This is not for beginners ********[/CENTER]**
[/SIZE]

[SIZE="3"][CENTER] This guide is to help people install the latest version of kiba-dock - THAT IS ALL - If it doesn't work I'm afraid I wont be able to help unless it is a problem with the install, any problems with kiba-dock working but not properly or fully is most likely a problem with the code since kiba-dock is under development and not that stable for many people. So any problems with the program itself please start a separate thread on this forum or on the kiba-dock forum [/CENTER][/SIZE]

[SIZE="4"]**[CENTER]******** You need to have beryl /  compiz - fusion working to install kiba-dock ********[/CENTER]**
[/SIZE]

[CENTER][SIZE="3"][COLOR="Blue"]Note For 64-Bit users[/COLOR][/SIZE]
[COLOR="Blue"]If you are using a 64 bit version of ubuntu I have added a small section to the how-to specifically for you, most steps are same both 32 bit and 64 bit apart one section of the code so please only do 64-bit stuff[/COLOR]
[COLOR="Red"] Warning : I myself do not use a 64-bit version of ubuntu so this is all done from help from other users - Please feel free to message me if any changes need to be made[/COLOR][/CENTER]

Hey everyone

I just managed to get kiba-dock installed and working on my computer and this is how i did it.

I must warn you - Im very new to compiling programs and this is my first how-to, i just hope this works for some people

p.s. the first part is from price-childs orig. thread on installing kiba-dock but has the python-gtk2-dev package added to end of the installed build packages- So thank you for this

First of all install the build depencies

```
sudo aptitude remove automake1.4
```

```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
```

Then make the directory to install kiba-dock into

```
mkdir kiba-dock
cd kiba-dock

```
```

svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/ akamaru

```
```

svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/ kiba-dock

```
```

svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/ kiba-plugins

```
```

svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/ kiba-dbus-plugins

```

************************ Not necessary to make Kiba-Dock to Work *********************************

I know the first SVN repo of the 2 below is for a gaim plugin, if you don't have gaim, then you don't need to worry about it - kiba-dock will run without.
I dont know what the ephy-extension is for and i didnt need to make it work.

```

svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-gaim-plugin kiba-gaim-plugin
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-ephy-extension kiba-ephy-extension

```

*****************************************************************************************************************

[CENTER][COLOR="Lime"]*****************************************************************************************************************[/COLOR]
[SIZE="4"][COLOR="Lime"]32-Bit Ubuntu Users[/COLOR][/SIZE][/CENTER]

Next just do the following - [SIZE="3"]**_Typing each line at a time_** [/SIZE]
```

cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
sudo make install
cd ..

```
```

cd kiba-dock/
./autogen.sh
sudo make install 
cd ..

```
```

cd kiba-plugins/
./autogen.sh
sudo make install 
cd ..

```
```

cd kiba-dbus-plugins/
./autogen.sh
sudo make install
cd ..

```
[CENTER][COLOR="Lime"]*****************************************************************************************************************[/COLOR]

[COLOR="Blue"]*****************************************************************************************************************[/COLOR]
[SIZE="4"][COLOR="Blue"]64-Bit Ubuntu Users[/COLOR][/SIZE][/CENTER]

```
cd akamaru/ 
./autogen.sh --prefix=/usr --exec-prefix=/usr --libdir=/usr/lib64 
sudo make install 
cd .. 
```

```

cd kiba-dock/ 
./autogen.sh --prefix=/usr --libdir=/usr/lib64
sudo make install 
cd .. 
```

```
cd kiba-plugins/ 
CC="gcc -fPIC" ./autogen.sh --prefix=/usr --libdir=/usr/lib64 
sudo make install 
cd .. 
```

```

cd kiba-dbus-plugins/ 
./autogen.sh --prefix=/usr --libdir=/usr/lib64 
sudo make install 
cd ..
```

[CENTER][COLOR="Blue"]*****************************************************************************************************************[/COLOR][/CENTER]

Now it should be installed and working ok (Fingers crossed)

Now all you have to do is type the following into a terminal and ur done

```
 kiba-dock 
```


[CENTER]**************************************** Adding To Start-Up *****************************************************************[/CENTER]

Most people want to have kiba-dock to start up with there computer - here is how

Go to System -> Preferences -> Sessions and click add new under the start-up tab. 

Name = Kiba-Dock
Command = kiba-dock

[CENTER]*****************************************************************************************************************[/CENTER]

If you have any problems (i.e. compiler errors i would suggest just typing a chunk of the error message into the search for the forums at [www.kiba-dock.org](www.kiba-dock.org)

***************** Un-Install ************************************

If for some reason you wish to un-install kiba-dock then so the following:

(You may need to change the cd command (Change Directory) if you installed kiba-dock in a different file to the one in the How-To)

Go into each sub-directory of kiba-dock folder and and type sudo make uninstall

```
cd kiba-dock/kiba-dbus-plugins
sudo make uninstall
cd ..

```

```

cd kiba-dock/kiba-plugins
sudo make uninstall
cd ..

```

```

cd kiba-dock/kiba-dock
sudo make uninstall
cd ..

```

```

cd kiba-dock/akamaru
sudo make uninstall

```

and your done

***************** Getting Akamaru Physics ************************************

Unfortunately the latest version of kiba-dock doesn't include the akamaru physics engine (The part that makes the icons do fun stuff)

Do get this simply do the following after completing the how-to above.

Then type the following

```

cd kiba-dock
svn update -r 602 *

```

And finally do the steps from the '32 bit Ubuntu Users' or '64 bit Ubuntu Users' onwards.

Hope this helps

Matt

---

### Post by mikibg on 2007-09-19
[http://www.youtube.com/watch?v=D3LRiQJ3IC0](http://www.youtube.com/watch?v=D3LRiQJ3IC0)
if some1 code in python we need him or her to change script for feeder and mail in kiba  TQ
[www.kiba-dock.org](www.kiba-dock.org)

---

### Post by Armadillo Kilr on 2007-09-19
it worked except when i typed in "kiba-dock" it started the dock but also said this in the terminal:

** Message: cant load file '/home/phil/.kiba-dock/config': Failed to open file '/home/phil/.kiba-dock/config': No such file or directory

and when i close the terminal, the dock closes as well

---

### Post by HokeyFry on 2007-09-19
add "kiba-dock" to the list of autostarted programs

it will solve the open terminal issue anyways

---

### Post by HokeyFry on 2007-09-19
after replying i just had to try this out

i love you man lol in a totally platonic way haha


no but this is a good howto, especially for your first one. keep it up and put up more ways to make my linux laptop more awesome ;)


peace

---

### Post by Armadillo Kilr on 2007-09-20
ok new problem. i added it to autostart, it runs without the terminal. but now there are two docks. one in the background of the other. the background dock does nothing, doesnt move, not aligned to the pointer when i right click to try to access the settings...

when i put physics on, the icons aren't aligned to the background image of the dock either. it bounces around and all, but like i said, double icons on the screen.

---

### Post by mattgaunt on 2007-09-20
armadilo kilr, i am no expert on kiba-dock so cant really help

But heres a suggestion, remove it from the autostart, now right click on ur top menu bar and select then do the following

Add New Launcher ->  Custom Launcher -> Fill in name and comment and set commmand to "kiba-dock" you can leave the icon for now

Then you should have a new launcher button on ur top menu bar, now just click on that and see if that works

I haven't had the 2 docks but i had the problem with when the physics engine was on the icons didn't line-up, i think it is because kiba-dock isn't the most stable of programs

Im only going by what I've done, all that said, im probably goin to be trying awm - a different dock, so ill try this out and if i like it over kiba-dock ill let you guys know and probs do a little how to on that

Cheers hokey fry - Glad you liked it, well ull have to try out compiz-fusion if u haven't already :)

Matt

---

### Post by Junkuhn on 2007-09-20
This is a great How-To, very strait forward. :) 
I do get an error though. When I do this:


> **mattgaunt said:**
> 
Next just do the following - Typing each line at a time
```

cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
sudo make install
cd ..

```

The second line to be specific. When I put that in, I get 

```

**Checking for intltool...**
***Error***: You must have intltool intalled to compile akamaru
```

What to do? :)

---

### Post by Lord Illidan on 2007-09-20
Install intltool from the repositories?

---

### Post by Junkuhn on 2007-09-20
> **Lord Illidan said:**
> Install intltool from the repositories?

Oh sorry, I forgot to mention: I installed Ubuntu yesterday in anger over my Vista crashed, so I'm not that familar with the terminal. :) 

I need thing explained like I'm a five-year old... :)

---

### Post by Junkuhn on 2007-09-20
Never mind I got it now.. thanks :)

---

### Post by Armadillo Kilr on 2007-09-20
hey so ever since i installed kiba-dock i boot my laptop and i have to log in TWICE. (???) i type in username and password, it goes black, then it goes back to login and i can login in the second time around. do you think it has anythign to do with the dock?

another thing, when i launch firefox it goes straight to a Bad 400 error and not to my homepage? 

thanks in advance and great tutorial cuz mine works other than those two weird issues:guitar:

---

### Post by mattgaunt on 2007-09-21
That is very very weird lol

I'm afraid i can't really help - all i can suggest is posting up any errors u get if u started kiba-dock from a terminal either here or kiba-dock.org forum

If any of you guys have compiz-fusion or beryl running on your computers i would definately suggest you try avant-window-manager (awn)

I installed it yesterday, it doesn't do any of the exciting kiba-dock physics stuff but the dock itself is pretty stable and simple to use

[https://launchpad.net/awn](https://launchpad.net/awn)

but u do have to have compiz-fusion or beryl running

Matt

---

### Post by Neo4 on 2007-09-21
How do i do to install only the gaim plugin? I have kiba dock installed but now it don't have the gaim plug in!

---

### Post by sjpritch25 on 2007-09-21
For that don't want to fuss with the terminal, you can install it via Synaptic Package Manager.  Just do a search for **kiba-dock** and install all the components.

---

### Post by Faud on 2007-09-24
Hi guys.. Everything was going good until this happened

ryan@ryan-desktop:~/kiba-dock/kiba-dock/akamaru$ ./autogen.sh --prefix=/usr --exec-prefix=/usr

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is unchanged
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy
Putting files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy
libakamaru_la_LDFLAGS: variable `export_symbols' is used but `export_symbols' is undefined
autoreconf: automake failed with exit status: 1
ryan@ryan-desktop:~/kiba-dock/kiba-dock/akamaru$ 

Any ideas? i did a google on it and found another website that had an unanswered thread with the same problem

Thanks

---

### Post by Faud on 2007-09-24
Got it figured out. 
Woot

:)

---

### Post by Uber Nooblett on 2007-09-30
> **Faud said:**
> Got it figured out. 
Woot

:)

any chance you could say how? I have the same error :(

---

### Post by Norrbagge on 2007-10-07
Well... i know plowed through your how-to and it all seem to be fine. But one problem though... 

When i was finished i got this error:

> ** Message: cant load file '/home/"User Name"/.kiba-dock/config': Feil under åpning av fil «/home/"User Name"/.kiba-dock/config»: No such file or directory


It appear on the bottom of my screen looking all good. but as soon as i close the Terminal it dissapear... Whats wrong??? i followed your how-to step by step... 

BTW: i am running Ubuntu Feisty Fawn 32nit with Compiz...

---

### Post by mattgaunt on 2007-10-07
I think if u try running kiba-dock with sudo at the start it may fix ur problem - but kiba-dock should still run anyway doesn't it??

But its not a vital error message - if u make a launcher on ur taskbar u wont see the error

Also u need to run the command as ```
kiba-dock &
``` and that means that when u close the terminal the program (In this case kiba-dock) will stay running

Hope that helps

Matt

---

### Post by Norrbagge on 2007-10-07
awesome... that works... i added the code so now it starts up along compiz fusion when i log inn... Thanks:)


EDIT: BUT as always, i have one more question... I used Object dock before changing to Ubuntu. When i used that i sorted the icons, if you know what i mean. This is something i cant figure out how to do with Kiba... Anyone got a tip for me to do this??? i also added the system tray to it, with two seperators between the icon and the tray... after rebooting the seperators was gone and the tray had changed from right to the left side...

---

### Post by Marty McFly on 2007-10-08
> **mattgaunt said:**
> 
*****************************************************************************************************************
Next just do the following - Typing each line at a time
```

cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
sudo make install
cd ..

```


When I got to the second line of that code, I got:
***Error***: You must have intltool installed to compile akamaru

What did I do wrong?

---

### Post by Gourgi on 2007-10-10
Thanks!!! 
clean, easy,  up-to-date how-to
kiba-dock installed with the instructions mentioned in ubuntu gutsy gibbon 7.10 beta
i just needed to add subversion 
> sudo apt-get install subversion

if you have more knowledge , just share it
now i go to play around ;)

---

### Post by drbob07 on 2007-10-11
This guide worked perfect for me! (And I'm running Gusty Gibbon)

So thank you :)

---

### Post by SabrinalovesUbun2 on 2007-10-12
Nice post, I will try it but I'm still a bit confused with the instructions.

---

### Post by mattgaunt on 2007-10-12
well any problems just give me a shout and ill do my best to help u out

---

### Post by mattgaunt on 2007-10-12
Hey Marty McFly you should be able to just type the following and then compile everything ok

```
sudo apt-get install intltool
```

Ive amended my how-to to install this anyway but this should work for you.

Sorry about the delay in time for me to reply

Matt

p.s. if my code above doesnt work just search intltool in synaptic package manager and install package from there - when i get time ill giv you a better idea on how-to do it

---

### Post by elgalloloco on 2007-10-13
Hi, a million thanx for this GREAT how-to....

This may be a dumb question, but....

How do i uninstall??

when i run the following command (sudo aptitude remove kiba-dock) in terminal i get this:

> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kiba-dock"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.



THANX!!

---

### Post by ileo on 2007-10-14
I installed it this morning and it works fine . One quick question how do I add a recycle bin to it ? And FYI: what I did to run it. I hit ALT+F2 and typed in Kiba-Dock and it runs fine after that. When I type it in the terminal I tried Kiba-Dock and Kiba-Dock & ,, and it would still shut down after closing the terminal .

Thank you for the tutorial it makes my screen look much better .

Here is a screenshot btw of my desktop

[IMG]http://i22.tinypic.com/2ypn714.png[/IMG]

---

### Post by mattgaunt on 2007-10-15
> **elgalloloco said:**
> Hi, a million thanx for this GREAT how-to....

This may be a dumb question, but....

How do i uninstall??

when i run the following command (sudo aptitude remove kiba-dock) in terminal i get this:



THANX!!

To un-install it you need to cd to the directory u put kiba-dock in (Where you ran all the sudo make install) and you need to type a command to remove it but cannot remember the command sorry

But just make a little thread in general and give a link to here and im sure someone will be able to tell you how to do it easily

Matt

---

### Post by Heartsblood on 2007-10-21
> **Faud said:**
> Hi guys.. Everything was going good until this happened

ryan@ryan-desktop:~/kiba-dock/kiba-dock/akamaru$ ./autogen.sh --prefix=/usr --exec-prefix=/usr

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal --output=aclocal.m4t
autoreconf: `aclocal.m4' is unchanged
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy
Putting files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy
libakamaru_la_LDFLAGS: variable `export_symbols' is used but `export_symbols' is undefined
autoreconf: automake failed with exit status: 1
ryan@ryan-desktop:~/kiba-dock/kiba-dock/akamaru$

Any ideas? i did a google on it and found another website that had an unanswered thread with the same problem

Thanks

> **Uber Nooblett said:**
> any chance you could say how? I have the same error :(

It means you're not using the right version of automake.  Make sure you have 1.9 installed.

---

### Post by Timsy321 on 2007-10-21
PROBLEM. 

When i run it either from the terminal or from alt F2, only the Kiba Dock folder opens up. The actually program wont start. What should i do?

im running Gusty Gibbon

Thanks in advance~!

---

### Post by NoPantsJim on 2007-10-22
Ignore this post, made a silly mistake and figured out how to fix it.

---

### Post by yesjoshyes on 2007-10-22
> **elgalloloco said:**
> Hi, a million thanx for this GREAT how-to....

This may be a dumb question, but....

How do i uninstall??

when i run the following command (sudo aptitude remove kiba-dock) in terminal i get this:



THANX!!

go to your kiba-dock sub-dir. (for me it was cd kiba-dock/kiba-dock)

then 

```
sudo make uninstall
```

hope this helps!

---

### Post by kakka256 on 2007-10-22
Thanks for a nice how-to. However i ran in to some trouble when trying to start the kiba-dock, namely:

(kiba-dock:31018): Gdk-CRITICAL **: gdk_cairo_create: assertion `GDK_IS_DRAWABLE (drawable)' failed

I'm kinda new to linux and just yesterday installed Gutsy Gibbon, so i don't really know what this means. I thought the gdk-stuff had something to do with Beryl or something (which i dont use).  I have the proeritary (spell.? :P) drivers for my ATIcard installed...

Any ideas?  Am i missing something?

---

### Post by mattgaunt on 2007-10-22
I think you need to have XGL installed to run kiba-dock.

So i think that might be your problem, honestly can't remember if it needs to be run on top of compiz-fusion (Which is the new program that has basically replaced beryl but i won't go into that lol)

I have a feeling you do need that installed but to install that you will need direct rendering to work which is done by installing the right drivers for your graphics card, ati or fglrx.

So best bet is to install the graphics card drivers. then install compiz-fusion (Which i believe comes with gutsy gibbon - I still need to upgrade from feisty so can't be sure but thats what i've heard in compiz-fusion forum from forlong) and then try re-installing kiba-dock

Hope this helps, sorry if its a bit wordy especially if your new to ubuntu so post another comment if i didnt make any sense

Matt

---

### Post by Korialstrasz on 2007-10-22
Hey, I'm trying to install kiba-dock on a friends computer and this happens at the end.

```

yuki@yuki-laptop:~/kiba-dock$ kiba-dock
Error (main.c @ line 1225):
        Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-path' command line parameter.

```

What exactly does this mean, I'm not very proficient with terminal "terms" yet.

---

### Post by Pdj79 on 2007-10-22
THANK YOU!!!!  I have been having such a hard time getting kiba-dock to install.  You tut did the trick.  Thanks.

---

### Post by JesseEklund on 2007-10-22
Great job on the guide it worked perfect for me first time thanks. One quick question about the dock. I would like to remove that annoying viewport switcher thing. The one that has the number of the current desktop your using. Ive searched through the settings a few times and cant seem to find anything but i know I'm missing something.

---

### Post by mattgaunt on 2007-10-23
Sorry dude, i know there is a way but i can't for the life of me remember, can u not just right click and remove it?? that or there is a tick box that just needs changing i think.

But i've changed to avant-window-navigator dock so not currently using it sorry

Matt

---

### Post by NukieNuggz on 2007-10-23
Hello,
 
          Hopefully someone can help me with a small problem. :) i was able to install kiba and it was working properly for quit awhile. Then i've decided to add kiba in the session menu, and when i did that, and restarted xserver.it broke.. Kiba wouldn't work,, I can't see the dock on my desktop, although i am able to get into the kiba setting , but the dock wouldn't display on my desktop nor the icons.. I'm running gusty gibbon, hopefully someone can help me out...thanks

---

### Post by qweac on 2007-10-23
Thanks for the guide mate. Not working properly here though! Get this error message when I try to start the dock:

erlend@qweac:~/kiba-dock$ kiba-dock
Error (main.c @ line 1225):
        Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-path' command line parameter.

---

### Post by mattgaunt on 2007-10-23
heya

Im afraid i can't really help with that error, the only thing i can suggest is to go to the official kiba-dock forums and search for that error msg and look for a fix

Matt

---

### Post by Seraph1 on 2007-10-23
I am with Qweac.

The same error occurs with my system. I have paid attention to all matters such as ./autogen.sh blah blah blah. But when I finally run the program the same error occurs. I also checked during the compiling if there were errors, of which there were. I am confused. I know it was recommended to ask the people at Kiba-Dock but I think it would be stupid in a way. I have seen errors and solutions but not exactly like this, and I don't want to be ridiculed. Some of those guys don't have the patience to answer a question. If anyone can help Qweac and myself, I would seriously appreciated it greatly. Thank you very much.

---

### Post by Seraph1 on 2007-10-23
By the way, 

     I have also copied the plugins into the directories where the missing files were not installed. I then tried one way of leaving them there, and the second time, installing the files there. But they didn't work. When I tried adding launchers to the icon, it wouldn't save and when I added a separator, there was a segmentation fault. This has also happened with AWM and I am completely stumped.

---

### Post by carlos1992 on 2007-10-24
Hey do you guys know if any Dock is available for Ubuntu 7.10 because is checked the website of Kiba-Dock and it says it doesn't support 7.10 yet so should i just wait or there is another option?:KS

---

### Post by mattgaunt on 2007-10-24
Qweac and seraph it seems like carlos has answered your question - if kiba-dock doesn't support 7.10 of ubuntu which i imagine you guys are most likely using.

You guys have 2 options, u can either re-vert back to ubuntu feisty fawn - I personally wouldn't recommend

or you install avant - window - navigator which is another dock program, not as 'Experimental' as kiba-dock in the sense that it doesnt have a physics engine but it is more stable in my opinion over kiba-dock

The link for how-to i used is here 

[http://ubuntuforums.org/showthread.php?t=385981&highlight=awn]("http://ubuntuforums.org/showthread.php?t=385981&highlight=awn")

I just compiled from source - but for gutsy gibbon i wud suggest using the repository as it states on the how-to

I have also been informed that awn is under better development than kiba-dock


Matt

p.s. i edited the tutorial to say not suitable for gutsy gibbon

---

### Post by mattgaunt on 2007-10-24
I just did some searching on the kiba-dock forum and found this [http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=555.0](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=555.0)

So carlos im afraid it is compatible with kiba-dock for some users.

According to the developer on the kiba-dock site he says that the latest svn version of kiba-dock isn't 100% working so ill give my how-to a go on gutsy gibbon 2night and let u all know what happens

Matt

---

### Post by mattgaunt on 2007-10-24
hey guys

Right i have just installed kiba-dock on my laptop which is running gusty gibbon

I did the exact same how-to and got everything to work, unfortunately the akamaru physics isnt working but that is known by the kiba-dock developer.

Matt

---

### Post by mattgaunt on 2007-10-24
qweac and seraph1 only thing i could suggest is if u guys try the following

When installing plugins instead of just autogen.sh try

./autogen.sh --prefix=/usr/local/lib/kiba-dock --exec-prefix=/usr/local/lib/kiba-dock

But i can't test and try this since it worked ok on my install

Sorry

Matt

---

### Post by qweac on 2007-10-24
> **mattgaunt said:**
> qweac and seraph1 only thing i could suggest is if u guys try the following

When installing plugins instead of just autogen.sh try

./autogen.sh --prefix=/usr/local/lib/kiba-dock --exec-prefix=/usr/local/lib/kiba-dock

But i can't test and try this since it worked ok on my install

Sorry

Matt

Thanks very much for the effort, but it's not working. :S

---

### Post by Afkpuz on 2007-10-24
> **Armadillo Kilr said:**
> 

another thing, when i launch firefox it goes straight to a Bad 400 error and not to my homepage? 





I'm not sure if you're still having this problem cause you asked it a while back in this thread, but here's how to fix it.  

Right click on the firefox launcher and select "edit"
Where it says "exec", make sure it says "firefox"  (by default, mine says "firefox 0"

There shouldn't be a zero after after it or anything else.  The command should simply read "firefox".  That should make it open to your default page.

---

### Post by mattgaunt on 2007-10-24
qweac i found a thread on kiba-dock forum for you and here might be the solution

Uninstall all the kiba-dock stuff - added how to do that to the end of the how too

Once you've done that install everything the same as u did before except instead of autogen.sh type

```
$./autogen.sh --prefix="/usr"
```

Grabbed it from here from someone else who had the error 

So give that ok but u must uninstall it all first

Matt

p.s. if this works - i told u to search the forums for help hee hee

---

### Post by TheBlackCat13 on 2007-10-24
I'm getting the following error when I try to make the plugins:

```
make  all-recursive
make[1]: Entering directory `/home/todd/programs/kiba-dock/kiba-plugins'
Making all in src
make[2]: Entering directory `/home/todd/programs/kiba-dock/kiba-plugins/src'
/bin/bash ../libtool --mode=execute /usr/bin/dbus-binding-tool --prefix=kiba_dock --mode=glib-server --output=kiba-dbus-glue.h kiba-dbus.xml
make  all-am
make[3]: Entering directory `/home/todd/programs/kiba-dock/kiba-plugins/src'
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -module -avoid-version -no-undefined  -o liblauncher.la -rpath /usr/local/lib/kiba-dock launcher-plugin.lo -lxml2 -lakamaru -lrsvg-2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lX11 -lXfixes -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0     liblauncher-type.la
gcc -shared  .libs/launcher-plugin.o -Wl,--whole-archive ./.libs/liblauncher-type.a -Wl,--no-whole-archive  /usr/lib/libxml2.so -lakamaru -lrsvg-2 /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so /usr/lib/libpangocairo-1.0.so -lXext -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libfreetype.so -lz -lfontconfig -lpng12 -lXrender -lX11 -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so  -Wl,-soname -Wl,liblauncher.so -o .libs/liblauncher.so
/usr/bin/ld: ./.libs/liblauncher-type.a(launcher.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
./.libs/liblauncher-type.a(launcher.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[3]: *** [liblauncher.la] Error 1
make[3]: Leaving directory `/home/todd/programs/kiba-dock/kiba-plugins/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/todd/programs/kiba-dock/kiba-plugins/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/todd/programs/kiba-dock/kiba-plugins'
make: *** [all] Error 2

```

I don't know why it happens, and it only happens with kiba-plugins.  Everything else compiles correctly.  It also happens when I do "make install" without doing make first.

---

### Post by Seraph1 on 2007-10-25
Thanks to Qweac, BlackCat and Matt....

       I am having the same errors as BlackCat and Qweac. Originally I tried installing the plugins to the /usr/... directory and the same error persisted. Also, I am having the same errors as BlackCat is and I just want to know if there are any other files required than the ones listed in the beginning of this tutorial. I am using Feisty Fawn, version 7.04 for a 64 bit laptop. I think if we could figure out the problems during compile time, them perhaps we can solve this issue once and for all. If any can help it would certainly be appreciated. Thank you to all.

---

### Post by Seraph1 on 2007-10-25
By the way ladies and gents....


      does this have anything to do with the errors for our kiba-dock package?

      Please add the files
      codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
      progtest.m4
      from the /aclocal directory to your autoconf macro directory
      or directly to your aclocal.m4 file.
      You will also need config.guess and config.sub, which you can get from
      [ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

      And if so, how do we circumvent this problem. I have absolutely no idea what to copy and how to because I am searching for some of those files and I find some, and then not. Any help would be grateful.

---

### Post by hopelessone on 2007-10-25
Is Kiba the same as AWN? do i need to uninstall AWN?

thanks

---

### Post by exchequer598 on 2007-10-25
Isn't Kiba-Dock more CPU intensive than AWN?

---

### Post by TheBlackCat13 on 2007-10-25
Seraph1, I was getting that error message when I ran autogen.sh for all 4 components, yet only the plugins failed to compile.  That leads me to believe that it is not the problem, but I can't be sure.

exchequer, the reason I am using Kiba is because it has better multi-monitor support.

hopelessone, there shouldn't be a problem with kiba and awn on the same computer.  I have them both installed on my computer at work without conflict.  Running them at the same time might be another story, though, but I can't say sinceI haven't tried.

---

### Post by mattgaunt on 2007-10-25
im sorry seraph1 i really dont kno what to suggest - only suggestion is that it may be because 64 bit processor

But to be honest i really dont know, do u have the 64 bit or the 32 bit version of ubuntu

Matt

---

### Post by TheBlackCat13 on 2007-10-25
I found [this](http://www.gentoo.org/proj/en/base/amd64/howtos/index.xml?part=1&chap=3) page describing the problem but it doesn't help me since it I don't understand it very well, I can't figure out how to apply the -fPIC option like they say, nor do I have any clue what "C[XX]FLAGS" is which appears to be a workaround.  Perhaps someone else can make some sense out of it.  It does appear to be an problem specific to x64 versions of linux, though.  I can tell you that case 2 is not the case for me, ./configure is definitely reporting that -fPIC is working.


This seems to be the relevant portions of the ./configure output
```
[b]checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes[/b]
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
[b]checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes[/b]
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
[b]checking for g77 option to produce PIC... -fPIC
checking if g77 PIC flag -fPIC works... yes[/b]
checking if g77 static flag -static works... yes
checking if g77 supports -c -o file.o... yes
checking whether the g77 linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate

```

(emphasis added to apparently relevant portions)

Just in the off chance it helps, I also get this message consistently when running autogen in all 4 cases:

```
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal
[b]/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
/usr/share/aclocal/oaf.m4:4:   run info '(automake)Extending aclocal'
/usr/share/aclocal/oaf.m4:4:   or see http://sources.redhat.com/automake/automake.html#Extending-acloca[/b]
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy
[b]/usr/share/aclocal/oaf.m4:4: warning: underquoted definition of AM_PATH_OAF
/usr/share/aclocal/oaf.m4:4:   run info '(automake)Extending aclocal'
/usr/share/aclocal/oaf.m4:4:   or see http://sources.redhat.com/automake/automake.html#Extending-aclocal[/b]
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
configure.in:12: installing `./missing'
configure.in:12: installing `./install-sh'
src/Makefile.am: installing `./depcomp'
autoreconf: Leaving directory `.'

```

Also, these are the only things that ./configure looks for but seems to be missing:

```
checking for sqrt... no
```

and

```
Build without PanelApplet Plugin!
```

All other checks appear to report yes (except for stuff like cross-compiling and big-endian).

---

### Post by santiagoward2000 on 2007-10-25
Hi,
First of all: Great how-to!!
Now, I'm sorry if this sounds a bit off-topic, but when I used Kiba in Feisty (from Treviño's repository), it had some cool plugins, like Stack. How can I get those in Gusty?
Thanks

---

### Post by rapsball4 on 2007-10-25
When I use the "sudo make install" for the last four (the first two are fine), I get errors.  The return from plugins is as follows:
```

Making install in src
make[1]: Entering directory `/home/ryan/kiba-dock/kiba-plugins/src'
make  install-am
make[2]: Entering directory `/home/ryan/kiba-dock/kiba-plugins/src'
/bin/bash ../libtool --tag=CC --mode=link gcc  -g -O2   -o liblauncher.la -rpath /usr/local/lib/kiba-dock/lib/kiba-dock -module -avoid-version -no-undefined launcher-plugin.lo -lxml2 -lakamaru -lrsvg-2 -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lX11 -lXfixes -lpango-1.0 -lcairo -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0     liblauncher-type.la 
gcc -shared  .libs/launcher-plugin.o -Wl,--whole-archive ./.libs/liblauncher-type.a -Wl,--no-whole-archive  /usr/lib/libxml2.so /usr/lib/libakamaru.so -lrsvg-2 /usr/lib/libgtk-x11-2.0.so /usr/lib/libgdk-x11-2.0.so /usr/lib/libatk-1.0.so /usr/lib/libgdk_pixbuf-2.0.so /usr/lib/libpangocairo-1.0.so -lXext -lXinerama -lXi -lXrandr -lXcursor -lXcomposite -lXdamage -lXfixes /usr/lib/libpango-1.0.so /usr/lib/libcairo.so /usr/lib/libfreetype.so -lz -lfontconfig -lpng12 -lXrender -lX11 -lm /usr/lib/libgobject-2.0.so /usr/lib/libgmodule-2.0.so -ldl /usr/lib/libglib-2.0.so  -Wl,-soname -Wl,liblauncher.so -o .libs/liblauncher.so
/usr/bin/ld: ./.libs/liblauncher-type.a(launcher.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
./.libs/liblauncher-type.a(launcher.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [liblauncher.la] Error 1
make[2]: Leaving directory `/home/ryan/kiba-dock/kiba-plugins/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/ryan/kiba-dock/kiba-plugins/src'
make: *** [install-recursive] Error 1
```

---

### Post by Seraph1 on 2007-10-25
Thanks goes to TheBlackCat and MattGaunt...

The package I am using is indeed Feisty Fawn 7.04 for the AMD 64 processor. I am unaware if that would create any issues as hand. By using the SVN downloads for kiba-dock I thought I would have been able to avoid this situation. The interesting thing is, at least I am not the only person with the same problem. TheBlackCat placed some information out on the compilation of the kiba-plugins and I get the same exact error. Of course, this only occurs when I install the plugins, not akamaru and kiba-dock itself. I am so puzzled because I am not sure if I need the other files that I listed earlier in this post for kiba-dock to actually work. I feel that we are almost close but still very far. Hmmmmm..... I will keep looking and seeing if there is a way to load it in properly, the only problem is I was mentioning the files which were requested during the compile in this thread, to keep it consistent with kiba-dock installation itself; however, I have looked elsewhere in this forum and have not found anything which can tell me how to install the missing files that I need when using the autogen.sh command. Any suggestions? :) Thanks for all your help.

---

### Post by qweac on 2007-10-25
> **mattgaunt said:**
> qweac i found a thread on kiba-dock forum for you and here might be the solution

Uninstall all the kiba-dock stuff - added how to do that to the end of the how too

Once you've done that install everything the same as u did before except instead of autogen.sh type

```
$./autogen.sh --prefix="/usr"
```

Grabbed it from here from someone else who had the error 

So give that ok but u must uninstall it all first

Matt

p.s. if this works - i told u to search the forums for help hee hee

Thanks again! Not working though... :P

---

### Post by rapsball4 on 2007-10-25
Although that wasn't aimed at me, I tried it too and got slightly farther.  The "sudo make install" for plugin is a bunch longer now before the same error.

---

### Post by santiagoward2000 on 2007-10-26
> **santiagoward2000 said:**
> Hi,
First of all: Great how-to!!
Now, I'm sorry if this sounds a bit off-topic, but when I used Kiba in Feisty (from Treviño's repository), it had some cool plugins, like Stack. How can I get those in Gusty?
Thanks

Hi,
I tried to compile it again, and see if there were any errors I hadn't pay attention to and I found this when I did ./autogen.sh for kiba-plugins:
```
NOT Building Plugins :
 volume - missing alsa
 dbus - missing dbus-glib-1
 gmenu - missing libgnome-menu
 stack - missing gnome-vfs-2.0
 stack - missing libgnomeui-2.0
 trash - disabled on configuration
```

I looked for those packages in Synaptic but couldn't find them. Do you know what I should do?

---

### Post by TheBlackCat13 on 2007-10-26
Put "lib" before each one, and if it already has lib look for another numbers.  So for instance it is libdbus-glib, libgnome-vfs,  The other ones are there, the numbers are just slightly different.  As for alsa just make sure you have alsa-base and alsa-utils installed.

---

### Post by santiagoward2000 on 2007-10-26
> **TheBlackCat13 said:**
> Put "lib" before each one, and if it already has lib look for another numbers.  So for instance it is libdbus-glib, libgnome-vfs,  The other ones are there, the numbers are just slightly different.  As for alsa just make sure you have alsa-base and alsa-utils installed.

Hi TheBlackCat13,
Look, I already had these packages:
[LIST]
[*]alsa-base
[*]alsa-utils
[*]libdbus-glib-1-2
[*]libgnome-menu2
[*]libgnomevfs2-0
[*]libgnomeui-0
[/LIST]

and still not working. :(

---

### Post by TheBlackCat13 on 2007-10-26
Alright, I looked into the -fPIC issue and found out how to get the compiler working at least for me.  I did a few things, so try them in sequence because I am not 100% sure which of them actually did it.  First, run this command:

echo $CFLAGS   

If you get nothing, run this:

CFLAGS=-fPIC;export CFLAGS 

If there is an output run this:

CFLAGS=$CFLAGS -fPIC;export CFLAGS

Then run "./autogen.sh" again.  Then run "make clean" and then "make" again.  If that works good.  If not repeat the whole process, except replace CLFAGS at every point with CXXFLAGS.  Don't forget to make clean again.  If that still doesn't work do it with CPPFLAGS.  If that still doesn't work try FFLAGS. I did not run make clean until I did it with all of them so I don't know which one actually fixed it.  They are listed in order of what I consider to be decreasing likliness.  Please report which one fixed it (or if it doesn't work at all) so we all know for the future.

---

### Post by mattgaunt on 2007-10-26
just an extra note on the part about the lib files, i had that similar sort of error and everythin still seemed to work ok, but anyway i hav a feeling that if there are any of the lib files but with -dev at the end u need to install those as well

Matt

---

### Post by Muscar on 2007-10-26
Thanks, it worked 	:mrgreen:

---

### Post by Seraph1 on 2007-10-26
Hello to all.

It's 5:02 am here, and I have been working out on this kiba-dock since about 1:30 am. After sitting here confused and close to taking a sledgehammer to my poor computer, I may have found something.

The following commands helped me with the compiling issues and helped install kiba-dock plugins....

cd akamaru/ &&
./autogen.sh --prefix=/usr --exec-prefix=/usr --libdir=/usr/lib64 &&
sudo make install &&
cd .. &&
cd kiba-dock/ &&
./autogen.sh --prefix=/usr --libdir=/usr/lib64 &&
sudo make install &&
cd .. &&
cd kiba-plugins/ &&
CC="gcc -fPIC" ./autogen.sh --prefix=/usr --libdir=/usr/lib64 &&
sudo make install &&
cd .. &&
cd kiba-dbus-plugins/ &&
./autogen.sh --prefix=/usr --libdir=/usr/lib64 &&
sudo make install &&
cd ..

Note however, that this is from another website which I almost did NOT find until I googled the liblauncher file.  All thanks goes to weibullguy of:

[http://www.linuxquestions.org/questions/linux-desktop-74/error-trying-to-install-kiba-dock-on-ubuntu-gutsy-64-594648/](http://www.linuxquestions.org/questions/linux-desktop-74/error-trying-to-install-kiba-dock-on-ubuntu-gutsy-64-594648/)

For this SIMPLE, STRAIGHT FORWARD help. I hope this can be of assistance to TheBlackCat and Qweac. Also, thanks to Matt for his wonderful assistance as well. I just wished that when people saw these errors, they could be a little more receptive to our pleas for help. Now all I have to figure out is how to add the launchers and everything should be great. Or else, I will drawing with a magic marker on my screen pretending to be cool instead of having the cool effects we all want.  :)

---

### Post by rapsball4 on 2007-10-26
Nice!  I started that thread there yesterday and just got mine working with that help as well, so I was coming here to link to it for anyone else with the problem.

Anyway, mine works, but there's a few glitchy things I need to work out - the main one being that the icons stay up when the menu hides if I turn on physics.  I'd like them to hide too, which I assume is possible.  I think I saw somewhere previously how to remove the Viewport viewer (and hopefully the clock and RAM monitor), so I'll dig back through and try to find that again later when I have more.  And I checked out Gnome Main Menu in the Settings, but it isn't showing up on the dock still.

---

### Post by maduranga on 2007-10-26
I don't find a kiba-plugins folder. what i have done wrong?

---

### Post by rapsball4 on 2007-10-26
Correct that last post by myself.  There wasn't a solution given for how to get rid of the Viewport Switcher, although I found the RAM monitor and the clock easily enough in the settings that I had somewhere skimmed over the first time.  Still no sign of GNOME Menu that I checked off - not sure if I want it anyway, but I'd like to at least check it out.  The physics still keep the icons from hiding, too, and not lining up right.

New problems: 
- A random white block with black border appeared at the end of the dock after I rebooted. It disappeared after turning the dock off and on again.  Haven't rebooted again since to try.
- If I put Firefox in the dock, and change it so that it'll show my homepage again (as answered earlier in thread), kiba closes when I close firefox again.  If I open it again after that, firefox is back off the dock.

---

### Post by kakka256 on 2007-10-26
> **mattgaunt said:**
> I think you need to have XGL installed to run kiba-dock.
...
So best bet is to install the graphics card drivers. then install compiz-fusion (Which i believe comes with gutsy gibbon - I still need to upgrade from feisty so can't be sure but thats what i've heard in compiz-fusion forum from forlong) and then try re-installing kiba-dock
...
Hi. Thanks for the reply, Matt, you were absolutely right. I had the correct drivers but had not setup the compiz or the xgl, didnt think i needed them. After installing xserver-.xgl kiba-dock starts fine. Thanks!

I did not get the dbus, stack, gmenu, trash or volume plugins though, exactly the same problem santiagoward2000 seems to have..

EDIT:  Adding the -dev files via synaptic of the "missing" lib-files seems to have sorted this problem!  Everything works fine now! Thanks alot, Matt.

---

### Post by santiagoward2000 on 2007-10-26
> **mattgaunt said:**
> just an extra note on the part about the lib files, i had that similar sort of error and everythin still seemed to work ok, but anyway i hav a feeling that if there are any of the lib files but with -dev at the end u need to install those as well

Matt

Hey! Thanks Matt!
That did it. I can't use some plugins like Trash or Gmenu, but that's probably because I'm using XFCE.
The only plugin I couldn't compile is volume, does anybody know what packages it needs? I already have alsa-base and alsa-utils.
One more question. What's the Firefox DBus plugin and how do I use it? I tried to enable it but nothing happaned.

---

### Post by panteraz on 2007-10-26
hm....

antonis@fidel:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/) kiba-dock
svn: PROPFIND request failed on '/svnroot/kibadock/trunk/kiba-dock'
svn: PROPFIND of '/svnroot/kibadock/trunk/kiba-dock': could not connect to server ([https://kibadock.svn.sourceforge.net](https://kibadock.svn.sourceforge.net))


I am getting this.. and I have internet of course... why ?

---

### Post by mrgoodkat on 2007-10-26
Thanks Matt, that tutorial ran beautifully on my Ubuntu 7.10 laptop! :D

---

### Post by ubuntios on 2007-10-27
Does anybody knows how to add a trash icon on the dock?

---

### Post by Vlux on 2007-10-27
New Gutsy user here. I typed in the command as listed, but when I input the svn part, it says it's not installed. So I typed it sudo apt-get install subversion and told me the subversion package couldn't be found. Any solutions? Thanks.

---

### Post by TheBlackCat13 on 2007-10-27
Are you sure the univers, multiverse, and restrictred repos are on?  It is showing up for me.

---

### Post by mattgaunt on 2007-10-27
Hey guys,

I've just edited the how-to to try and help out 64-bit users if anyone spots any problems please please give me a shout

Matt

---

### Post by Bionic Apple on 2007-10-27
When I try to uninstall Kiba-dock, all of the files are left in my home folder!  How do I delete them?  No matter what I try to do, the folder and it's contents won't go away.

---

### Post by rapsball4 on 2007-10-27
> **Bionic Apple said:**
> When I try to uninstall Kiba-dock, all of the files are left in my home folder!  How do I delete them?  No matter what I try to do, the folder and it's contents won't go away.

My kiba-dock kept reappearing, even after I removed it from startup and went through the uninstallation procedure.  I ended up reinstalling Gutsy completely today before installing AWN (my patience wasn't enough to wait to try Cairo when so many good things are said about AWN).  I would recommend waiting to see if somebody else has a nicer solution, though (unless you are as impatient as me).

---

### Post by mattgaunt on 2007-10-28
Only thing i can suggest is using some command like ```
sudo rm /kiba-dock/
```

Only difference being that u may need to change /kiba-dock/ to what ever directory your trying to delete and i think this is the commmand cos i honestly only used a few times since installing ubuntu and cant remember it for sure

Matt

---

### Post by insaneidiot on 2007-10-28
Does anyone know how to remove the time and RAM usage apps from the dock?  I don't need them as they're already in my top pane.  Also, when I change the name of the application and click save, the dock quits itself and when I reload it, there is no change in the name.

---

### Post by Hexxagon on 2007-10-28
right-click on the dock, then Kiba Settings and then you just need to deactivate time and ram-usage (the menu bar on the left... scroll down a bit)

---

### Post by insaneidiot on 2007-10-28
OOOK.  I'm a dumbass.  Thanks :)

---

### Post by 23tv on 2007-10-28
how to config kiba to be like this:

[http://youtube.com/watch?v=bYsxaMyFV2Y](http://youtube.com/watch?v=bYsxaMyFV2Y)

thanks... i mean the dock shape and how the text appears with you put your mouse on them and the effect, etc,etc,etc

thanks

---

### Post by ubuntios on 2007-10-28
I'm trying to add the dock to the start up with this command :
 /home/username/.kiba-dock/kiba-dock  , but is not working , 
what I do wrong? 

Thnax

---

### Post by insaneidiot on 2007-10-28
> **ubuntios said:**
> I'm trying to add the dock to the start up with this command :
 /home/username/.kiba-dock/kiba-dock  , but is not working , 
what I do wrong? 

Thnax

To add Kiba to your start up, just go to System>Preferences>Sessions and click add new.  The command for the Kiba dock is "kiba-dock"

---

### Post by 23tv on 2007-10-28
how to config kiba to be like this:

[http://youtube.com/watch?v=bYsxaMyFV2Y](http://youtube.com/watch?v=bYsxaMyFV2Y)

thanks... i mean the dock shape and how the text appears with you put your mouse on them and the effect, etc,etc,etc

thanks

---

### Post by gmanpsycho on 2007-10-29
Thanks bunches.... I had to upgrade my PC to Gutsy after my Feisty went bananas on me... still not sure what really happened. Any way thanks for the HowTo.:guitar:

---

### Post by thousandpimps on 2007-10-29
it installed fine and i used it too but when i type kiba-dock in terminal it shows me this erroe:

Error (tray.c @ line 140):
        another systray already running

Error (plugin.c @ line 207):
        '/usr/local/lib/kiba-dock/libtray.so' is not loadable

---

### Post by mattgaunt on 2007-10-29
hey thousandpimps, i think it is because the system tray will only work on kiba-dock providing that u dont have the system tray running anywhere else i.e. gnome system tray on your normal panel

Matt

---

### Post by thousandpimps on 2007-10-29
iam still new to ubuntu...so what can i do to solve this problem and make kiba dock start when i start ubuntu

---

### Post by duncan.hawthorne on 2007-10-29
dear thousandpimps

make the panel work:
right click on the notification area on your panel and clikc remove, then restart kiba-dock

kiba-dock autostart 
go into:
gnome main menu>system>preferences>sessions>startup programs>new
and type kiba-dock as the command and kiba-dock as the description

---

### Post by duncan.hawthorne on 2007-10-29
for anyone struggling with things not working, i did a fresh install of gutsy recently and to get kiba-dock working i did: 

sudo apt-get install subversion buildessential: build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch subversion libapr1 libaprutil1 libpq5 libsvn1 subversion autoconf automake1.7 autotools-dev gettext m4 fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev  libglitz-glx-dev  librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev libdbus-1-dev libdbus-glib-1-dev gnome-vfs-extfs libgnome-menu-dev   libavahi-client-dev libavahi-common-dev libavahi-glib-dev libgcrypt11-dev   libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev liblzo2-dev  libopencdk8-dev libselinux1-dev libsepol1-dev libtasn1-3-dev  libaudiofile-dev libbonobo2-dev libbonoboui2-dev libcairomm-1.0-dev  libesd0-dev libgail-dev libgconfmm-2.6-1c2 libgconfmm-2.6-dev  libglademm-2.4-1c2a libglademm-2.4-dev libglibmm-2.4-dev  libgnome-keyring-dev libgnome-vfsmm-2.6-1c2a libgnome-vfsmm-2.6-dev  libgnome2-dev libgnomecanvas2-dev libgnomecanvasmm-2.6-1c2a  libgnomecanvasmm-2.6-dev libgnomemm-2.6-1c2a libgnomemm-2.6-dev  libgnomeui-dev libgnomeuimm-2.6-1c2a libgnomeuimm-2.6-dev libgtkmm-2.4-dev  libhal-dev libhal-storage-dev libjpeg62-dev libsigc++-2.0-dev

this is probably a few more packages than are strictly necessary, and a load you will already have installed (it will ignore these packages), but it should do the trick.

once the packages are installed.... try the guide again. this time everything will compile

---

### Post by thousandpimps on 2007-10-29
sorry to ask this simple question  but hmm where the notification area? and when u say panel do u mean like the place where there is applications places system at the top of my monitor.|?

---

### Post by ubuntios on 2007-10-29
> **insaneidiot said:**
> To add Kiba to your start up, just go to System>Preferences>Sessions and click add new.  The command for the Kiba dock is "kiba-dock"


Thanx It works fine now :)

---

### Post by duncan.hawthorne on 2007-10-29
panel = thing at top of screen
notification area = vertical lines on right of magnifying glass and the computers icon to the right. equivalent of the system tray in windows

a good tip for next time though: ask google

however, my guess, if you dont know what it is, you probably dont want it on the dock (errors you get when you run arent necessarily bad, if you dont notice something missing or something not working, just ignore them, they are probably stuff you dont need to read)

---

### Post by mattgaunt on 2007-10-29
The bit on your top bar where u have the network manager, that is displayed in your systray, same as if u run pidgin or kopete, u can minimize it to the system tray.

So by getting rid of the systray in your panel (Top bar) then it should work on kiba-dock. But as  duncan-hawthorne said, if you don't know what it is then probs best u dont tamper till you get more used to ubuntu.

But then again u can make the mistake and learn from it. -> Your choice dude :-) - We'll be here to help you out if sumthin did go wrong

Matt

---

### Post by distratios on 2007-10-31
Hi!

I use the latest ati driver on Kubuntu 7.10. Hence, I run compiz without xgl (xserver-xgl). Do I have to build kiba-dock with libglitz-devel? I' am not shure, if this will cause any troubles, since I'm not running libglitz.

---

### Post by mattgaunt on 2007-10-31
Im afraid i dont know what libglitz is :-S

All i can say is that if u need it to run kiba-dock then kiba-dock wont install when you try to compile it, so all i can suggest is try it and see if it works.

Matt

---

### Post by TheWired on 2007-10-31
Very nice guide. Everything seemed to work pretty well on the install aside from having to add sudo to almost everything. I did get that config error that I noticed a few people posting about in previous threads. It fixed itself after I added kiba-dock to startup and rebooted. It will write the config file it is looking for during startup. 

...Now to just configure it!

---

### Post by Tavorisch on 2007-10-31
Okay ,, I think what this post needs is a little how to on a startup script.. I find that
it works best if started AFTER beryl on startup.. just a simple little .sh start script will do!
worked for me.. just open up terminal and type "gedit kibastart.sh and copy and paste ```

#!/bin/bash
sleep 5
kiba-dock

```
Save and close
in terminal again type "chmod a+x kibastart.sh" to make sure its executable
Then, System>Preferences>Sessions Add this to command, "/home/YOURUSERNAME/kibastart.sh"
log out then login see if it helped, the number after the sleep command is in seconds
so lower or lengthen as you need. mine is at 2 i have attached screen shot to conky
coming in last at sleep 6  is conky my desktop terminal wouldn't start with conky any lower
so you can see how certain things affect attaching to the desktop.. check out screen shot!

---

### Post by greg142 on 2007-10-31
followed the everything exactly how ya say it but still get this error msg and kiba wont start

Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-pa
anyone help me out
i'm running 32bit

---

### Post by duncan.hawthorne on 2007-11-01
[http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.msg2613#msg2613](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.msg2613#msg2613)

quick script for installing on ubuntu is located here, might be useful for anyone having trouble

---

### Post by Lunks on 2007-11-02
For some reason, my settings aren't being applied. After some tests, looks like everything can be enabled, but aren't disabled until restart.

---

### Post by Baby Boy on 2007-11-02
After following all the instructions and installing Kiba-Dock, I can only turn it on when I type > kiba-dock in the terminal and when I close the terminal it closes too. I have added the command to autostart kiba-dock in the *System->Preferences->Sessions* but nothing happens. Any suggestions? :confused:

---

### Post by mattgaunt on 2007-11-02
You should just add it to the sessions under the start-up tab

Name: Kiba-Dock
Command: kiba-dock
Comment: Dock Program

What did u  put on the start-up session??

Gaunt

---

### Post by duncan.hawthorne on 2007-11-02
@babyboy
if you launch any app from terminal, when you close terminal, you close the app
this is just how linux works
if you do alt+f2 you can get a run dialogue wherre you can run kiba-dock without a terminal (also clicking the gnome main menu>accesories>kiba-dock should also do this

@greg142
try symlinking /usr/local/lib/kiba-dock to /usr/lib/kiba-dock (looks like the plugins are being installed in the wrong folder)
ie run:
sudo ln -s /usr/lib/kiba-dock /usr/local/lib/kiba-dock

---

### Post by Baby Boy on 2007-11-03
> **duncan.hawthorne said:**
> @babyboy
if you launch any app from terminal, when you close terminal, you close the app
this is just how linux works
if you do alt+f2 you can get a run dialogue wherre you can run kiba-dock without a terminal (also clicking the gnome main menu>accesories>kiba-dock should also do this
Yeah, alt+F2 makes it run without terminal. Can't believe I didn't know about that until now, thanks for the tip.

> **mattgaunt said:**
> You should just add it to the sessions under the start-up tab

Name: Kiba-Dock
Command: kiba-dock
Comment: Dock Program

What did u  put on the start-up session??

Gaunt
That's exactly what I put in the start-up session (without the *Comment*) and it doesn't start. :-k

---

### Post by duncan.hawthorne on 2007-11-03
@babyboy
capitals do matter, so if the command you used was Kiba-dock it is wrong
you could also (instead of typing in kiba-dock) you could browse to the file in the startup programs dialogue and add it that way., ie browse to /usr/bin/kiba-dock (or perhaps /usr/local/bin/kiba-dock). however the two ways are entirely equivalent so this would be just making sure you have made a typo

perhaps the dock is failing to start up because it is loading before compiz is running. so look at the post by Tavorisch, ie post #108. this should fix it

---

### Post by mattgaunt on 2007-11-03
Just a note too everyone, i know several users post things like scripts and so on but i am seriously reluctant to put it as part of the how-to since i didnt need it and i have no idea if it fixes any problems, so if you guys have a problem, then find a fix please please please just send me a message and ill more than happily add it to the how-to

But unless i know it works i dont want to add it

Gaunt

---

### Post by Baby Boy on 2007-11-03
> **duncan.hawthorne said:**
> @babyboy
capitals do matter, so if the command you used was Kiba-dock it is wrong
you could also (instead of typing in kiba-dock) you could browse to the file in the startup programs dialogue and add it that way., ie browse to /usr/bin/kiba-dock (or perhaps /usr/local/bin/kiba-dock). however the two ways are entirely equivalent so this would be just making sure you have made a typo

perhaps the dock is failing to start up because it is loading before compiz is running. so look at the post by Tavorisch, ie post #108. this should fix it
Thanks a lot, that did help! :)

> **mattgaunt said:**
> Just a note too everyone, i know several users post things like scripts and so on but i am seriously reluctant to put it as part of the how-to since i didnt need it and i have no idea if it fixes any problems, so if you guys have a problem, then find a fix please please please just send me a message and ill more than happily add it to the how-to

But unless i know it works i dont want to add it

Gaunt
I had to do this to make kiba-dock autostart:

Tavorisch's post
> [SIZE="1"]Okay ,, I think what this post needs is a little how to on a startup script.. I find that
it works best if started AFTER beryl on startup.. just a simple little .sh start script will do!
worked for me.. just open up terminal and type "gedit kibastart.sh and copy and paste
Code:

#!/bin/bash
sleep 5
kiba-dock

Save and close
in terminal again type "chmod a+x kibastart.sh" to make sure its executable
Then, System>Preferences>Sessions Add this to command, "/home/YOURUSERNAME/kibastart.sh"
log out then login see if it helped, the number after the sleep command is in seconds
so lower or lengthen as you need. mine is at 2 i have attached screen shot to conky
coming in last at sleep 6 is conky my desktop terminal wouldn't start with conky any lower
so you can see how certain things affect attaching to the desktop.. check out screen shot![/SIZE]



I also have another quick question. I was so happy I got kiba-dock to work I immediately started messing with the config. How can I get all the settings back to default? (I've tried reinstalling)

---

### Post by Showpan on 2007-11-06
I can not install it,as follows:
root@Showpan:~/kiba-dock# svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru
Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? accept permanently
svn: PROPFIND request failed on '/svnroot/kibadock/trunk/akamaru'
svn: PROPFIND of '/svnroot/kibadock/trunk/akamaru': Server certificate verification failed: issuer is not trusted ([https://kibadock.svn.sourceforge.net](https://kibadock.svn.sourceforge.net))

 What should I do?
 THX

---

### Post by mattgaunt on 2007-11-06
showpan i think u typed 'accept permanently'

You need to jus type 'p' and then press enter to accept the certificate

Gaunt

---

### Post by jimerickso on 2007-11-06
mattgaunt:
i am having trouble with akamaru. whenever i enable it (at default settings) all the icons go from the dock to the left side of the screen and then fall off the screen on by one. do you have any tips or tricks concerning this problem? thank you very much!

---

### Post by mattgaunt on 2007-11-06
Nah sorry

Unfortunately kiba-dock is under heavy development and is very un-reliable

The developer is re-working alot of the code and alot of it isnt working or being re-done

Gaunt

---

### Post by santiagoward2000 on 2007-11-06
> **jimerickso said:**
> mattgaunt:
i am having trouble with akamaru. whenever i enable it (at default settings) all the icons go from the dock to the left side of the screen and then fall off the screen on by one. do you have any tips or tricks concerning this problem? thank you very much!

Hi! I get this same problem sometimes. I just turn it off and back on, that normally fixes it for me...

---

### Post by duncan.hawthorne on 2007-11-07
> **mattgaunt said:**
> Nah sorry

Unfortunately kiba-dock is under heavy development and is very un-reliable

The developer is re-working alot of the code and alot of it isnt working or being re-done

Gaunt


i dont know, seems pretty reliable to me.. just the physics part seems a bit shaky when you have some settings (unfortunately the defualt settings are one of the many the act oddly). Everything else works great though

---

### Post by jimerickso on 2007-11-07
> **duncan.hawthorne said:**
> i dont know, seems pretty reliable to me.. just the physics part seems a bit shaky when you have some settings (unfortunately the defualt settings are one of the many the act oddly). Everything else works great though
duncan.hawthorne:
what exactly are your akamaru settings??

---

### Post by mattgaunt on 2007-11-07
chances are alot has changed duncan.hawthorne since i last used it.

But last time i checked out kiba-dock.org the developer was having a massive re-write of alot of his code.

Im currently not using it because i needed something i little more reliable so started using awn, unfortunately doesnt have the akamaru fun but it works well so i cant complain.

But feel free to help each other out anyway with what works and doesnt work for you all

Gaunt

---

### Post by robcarr2 on 2007-11-08
Confirming that this worked in Ubuntu 7.10 :)

---

### Post by Kedster on 2007-11-10
i get an error lol i am a beginner at coding but got some experience

```
kedster@kedster-laptop:~$ cd kiba-dock/
kedster@kedster-laptop:~/kiba-dock$ ./autogen.sh
bash: ./autogen.sh: No such file or directory

```



im in gutsy gibin

---

### Post by Redenbacher on 2007-11-10
All this is fine and dandy, the install went very clean on Gutsy. But how do you install the kiba-gaim-plugin? I tried and it says 

checking for PIDGIN... configure: error: Package requirements (pidgin >= 1.2.0 pidgin < 3.0.0) were not met:

No package 'pidgin' found
No package 'pidgin' found

   I get this when I run ./autogen.sh in the kiba-gaim-plugin file created from this howto. Any ideas?

---

### Post by santiagoward2000 on 2007-11-10
> **Redenbacher said:**
> All this is fine and dandy, the install went very clean on Gutsy. But how do you install the kiba-gaim-plugin? I tried and it says 

checking for PIDGIN... configure: error: Package requirements (pidgin >= 1.2.0 pidgin < 3.0.0) were not met:

No package 'pidgin' found
No package 'pidgin' found

   I get this when I run ./autogen.sh in the kiba-gaim-plugin file created from this howto. Any ideas?

Well, according to [http://www.kiba-dock.org/]("http://www.kiba-dock.org/")

> does it work for pidgin
not yet, but it needs not much changes i guess

That's all I could find, but it's a post from May 18, 2007. I couldn't find anything newer (and I haven't actually tried installing that plugin...)

---

### Post by Redenbacher on 2007-11-11
That's a shame because that's the one thing I really need on my dock lol. I can never tell if I have a new message if I'm doing something at the same time!

 AWN has an alert for it, but AWN doesn't work and when it does it's buggy as hell.

---

### Post by mikibg on 2007-11-11
how to install kiba-dock is here in serbian LOL
[http://www.ubuntu-rs.org/forum/viewthread.php?tid=2739]("http://www.ubuntu-rs.org/forum/viewthread.php?tid=2739")

---

### Post by NukieNuggz on 2007-11-11
Hey guys, I managed to install kiba in 7.10 gusty gibbon, and at first it was running with no problem, but now it seem that i get an error everytime i tried to load kiba in the terminal. Has anyone experience this same error?

```
Traceback (most recent call last):
  File "/usr/local/share/kiba-dock/dbus_scripts/kiba-feeder.py", line 6, in <module>
    import feedparser
ImportError: No module named feedparser
*** stack smashing detected ***: kiba-dock terminated
Aborted (core dumped)

```

---

### Post by Kedster on 2007-11-11
i get an error lol i am a beginner at coding but got some experience

Code:

kedster@kedster-laptop:~$ cd kiba-dock/
kedster@kedster-laptop:~/kiba-dock$ ./autogen.sh
bash: ./autogen.sh: No such file or directory



im in gutsy gibin

please help i really like the dock effect please help

---

### Post by Showpan on 2007-11-13
Good!
It's very wonderful wth kiba-dock, I think it is more functional than AWN.
Thanks!:guitar:

---

### Post by jimerickso on 2007-11-13
can anyone provide some settings that will allow akamaru to run in a stable manner?? my icons are all over the place depending on the settings.

---

### Post by exactopposite on 2007-11-13
thanks a lot for this. i followed the howto  and it's working fine in 32bit gutsy.

---

### Post by macaholic on 2007-11-13
I'd just like to point out a script I have always had succes w/ on Ubuntu 7.10 (32 bit)
It also makes it very easy to update kiba aswell.
[http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=274.0](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=274.0)

---

### Post by SomeGuyDude on 2007-11-13
Okay, I like this thing okay but I've got some more than minor griefs.

1) Can it be themed at all? AWN's easy to throw themes on, this seems like you have to it yourself.

2) Where's the plugins? I don't see an option for them anywhere.

3) Trash icon?

---

### Post by ncappel1 on 2007-11-14
i had to stop at 
```
cd kiba-dock/
./autogen.sh
sudo make install 
cd ..
```
i am getting this error:
checking for DBUS... configure: error: Package requirements (dbus-glib-1) were not met:

No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



when i search for that package in synaptic, it is not found...
insights, anyone?

---

### Post by piratesmack on 2007-11-15
> **ncappel1 said:**
> i had to stop at 
```
cd kiba-dock/
./autogen.sh
sudo make install 
cd ..
```
i am getting this error:
checking for DBUS... configure: error: Package requirements (dbus-glib-1) were not met:

No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.



when i search for that package in synaptic, it is not found...
insights, anyone?

Yeah, I'm getting the same error now, too. It was just working yesterday

---

### Post by duncan.hawthorne on 2007-11-15
when compiling things need dependency eg dbus-glib-1
try:
dbus-glib-1
libdbus-glib-1
dbus-glib-1-dev
libdbus-glib-1-dev

one of those will work :)

i also quote my previous post:
"for anyone struggling with things not working, i did a fresh install of gutsy recently and to get kiba-dock working i did:

sudo apt-get install subversion buildessential: build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch subversion libapr1 libaprutil1 libpq5 libsvn1 subversion autoconf automake1.7 autotools-dev gettext m4 fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev libdbus-1-dev libdbus-glib-1-dev gnome-vfs-extfs libgnome-menu-dev libavahi-client-dev libavahi-common-dev libavahi-glib-dev libgcrypt11-dev libgnomevfs2-dev libgnutls-dev libgnutlsxx13 libgpg-error-dev liblzo2-dev libopencdk8-dev libselinux1-dev libsepol1-dev libtasn1-3-dev libaudiofile-dev libbonobo2-dev libbonoboui2-dev libcairomm-1.0-dev libesd0-dev libgail-dev libgconfmm-2.6-1c2 libgconfmm-2.6-dev libglademm-2.4-1c2a libglademm-2.4-dev libglibmm-2.4-dev libgnome-keyring-dev libgnome-vfsmm-2.6-1c2a libgnome-vfsmm-2.6-dev libgnome2-dev libgnomecanvas2-dev libgnomecanvasmm-2.6-1c2a libgnomecanvasmm-2.6-dev libgnomemm-2.6-1c2a libgnomemm-2.6-dev libgnomeui-dev libgnomeuimm-2.6-1c2a libgnomeuimm-2.6-dev libgtkmm-2.4-dev libhal-dev libhal-storage-dev libjpeg62-dev libsigc++-2.0-dev

this is probably a few more packages than are strictly necessary, and a load you will already have installed (it will ignore these packages), but it should do the trick.

once the packages are installed.... try the guide again. this time everything will compile"
i managed to compile it today doing this




Also the code may have a bug in it. you should maybe try updating to the latest version by doing svn up in the kiba-dock top level directory to update all the source, then try again

---

### Post by mikibg on 2007-11-15
if u want to install kiba-dock from svn u need
 ```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
```


some1 try to install kiba-dock with --enable glitz

---

### Post by ncappel1 on 2007-11-15
> **mikibg said:**
> if u want to install kiba-dock from svn u need
 ```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
```

sweet! This did the trick for me i installed all the packages in the list I didn't have, and was able to compile perfectly well. Now I just have to figure out how to optimize kiba-dock...

thank you!

---

### Post by piratesmack on 2007-11-15
> **mikibg said:**
> if u want to install kiba-dock from svn u need
 ```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
```


some1 try to install kiba-dock with --enable glitz

Nice! Worked like a charm.

---

### Post by piratesmack on 2007-11-15
> **piratesmack said:**
> Nice! Worked like a charm.

Ok I'm having a problem. The kiba dock icons appear as white squares when I enable physics. This might (I hope) be because of some compiz-fusion plugins I installed.

---

### Post by piratesmack on 2007-11-15
I'm about to do a fresh install of gutsy and I'll retry

---

### Post by piratesmack on 2007-11-16
Ok it's still happening. 

All the icons appear as white squares only when I start kiba dock with physics enabled. If I disable then re-enable physics, it works fine. This is a little annoying, any suggestions?

---

### Post by mikibg on 2007-11-16
akamaru is now little broken but daniel fix this soon ...
if u want to kiba works faster do not use shadow effects
kiba can not start or give some errors type in terminal 
kiba-dock --verbose 
and u find what is u problem

[http://www.youtube.com/watch?v=D3LRiQJ3IC0](http://www.youtube.com/watch?v=D3LRiQJ3IC0) 
maybe my video help u how 2 use kiba-dock

---

### Post by ncappel1 on 2007-11-16
> **piratesmack said:**
> Ok it's still happening. 

All the icons appear as white squares only when I start kiba dock with physics enabled. If I disable then re-enable physics, it works fine. This is a little annoying, any suggestions?

Just for the record, I didn't install with --enable glitz. if you did this, could it be causing your problem?

---

### Post by mikibg on 2007-11-16
no ...def is without glitz but u can compile kiba-dock with glitz
for amarok script go to after u install kiba-dock ..>kiba>kiba-dbus-plugins>scripts rename kiba-amarok.py.in to kiba-amarok.py and copy to  $(HOMEDIR)/.kde/share/apps/amarok/scripts
open amarok script manager and run kiba-amarok.py :)
maybe u need to reboot kiba
[IMG]http://img89.imageshack.us/img89/3635/screenshot1zy8.png[/IMG]

---

### Post by mattgaunt on 2007-11-16
hey mikibg jus wanted to say u hav an awesome set-up!!!!

What does the --enable glitz do exactly??

Gaunt

p.s. ill update the how-to to include the extra libraries since there is no harm in including them in the how-to

---

### Post by piratesmack on 2007-11-16
> **ncappel1 said:**
> Just for the record, I didn't install with --enable glitz. if you did this, could it be causing your problem?

No, I didn't either. I just followed the guide, but used the command that one guy posted instead of the one in the tutorial. A few days ago, I was able to follow this guide exactly without any errors. And kiba would start with physics enabled no problem.

---

### Post by mikibg on 2007-11-16
when u install kiba with glitz ....kiba is much faster
vlc works nice with compiz :) i like upload video in youtube
[http://www.youtube.com/watch?v=nrMTbAy83A4](http://www.youtube.com/watch?v=nrMTbAy83A4)

---

### Post by piratesmack on 2007-11-16
Well I've been messing with the kiba settings and I fixed my problem. Not sure what I did, but the point is it's fixed.

---

### Post by piratesmack on 2007-11-16
> **mikibg said:**
> when u install kiba with glitz ....kiba is much faster
vlc works nice with compiz :) i like upload video in youtube
[http://www.youtube.com/watch?v=nrMTbAy83A4](http://www.youtube.com/watch?v=nrMTbAy83A4)

What theme do you have installed?

---

### Post by mikibg on 2007-11-16
i use neutronium-GTK2  ...do not use emerald themes and this is vlc 0.9.0

---

### Post by mikibg on 2007-11-16
new 1 u get mixer in right click on volume plugin in dock and this is great stuf

---

### Post by amadeus266 on 2007-11-18
Anyone else getting this when running make in the plugins directory?
```

launcher-plugin.c:31:31: error: kiba-desktop-icon.h: No such file or directory
In file included from launcher-plugin.c:34:
launcher.h:80: error: expected declaration specifiers or '...' before 'KibaDesktopIcon'
launcher.h:82: error: expected declaration specifiers or '...' before 'KibaDesktopIcon'
launcher.h:90: error: expected declaration specifiers or '...' before 'KibaDesktopIcon'
launcher.h:93: error: expected declaration specifiers or '...' before 'KibaDesktopIcon'
launcher.h:101: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
launcher.h:104: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
launcher.h:107: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
launcher-plugin.c:40: error: expected ')' before '*' token
launcher-plugin.c: In function 'dock_object_size_cb':
launcher-plugin.c:145: error: 'KibaDesktopIcon' undeclared (first use in this function)
launcher-plugin.c:145: error: (Each undeclared identifier is reported only once
launcher-plugin.c:145: error: for each function it appears in.)
launcher-plugin.c:145: error: 'icon' undeclared (first use in this function)
launcher-plugin.c: In function 'object_size_factor_cb':
launcher-plugin.c:162: error: 'KibaDesktopIcon' undeclared (first use in this function)
launcher-plugin.c:162: error: 'icon' undeclared (first use in this function)
launcher-plugin.c: In function 'launcher_window_opened_cb':
launcher-plugin.c:228: error: 'KibaDesktopIcon' undeclared (first use in this function)
launcher-plugin.c:228: error: 'icon' undeclared (first use in this function)
launcher-plugin.c:243: error: 'check_icon' undeclared (first use in this function)
launcher-plugin.c:265: error: 'KIBA_DESKTOP_STATE_ACTIVE' undeclared (first use in this function)
launcher-plugin.c: In function 'launcher_window_closed_cb':
launcher-plugin.c:279: error: 'KibaDesktopIcon' undeclared (first use in this function)
launcher-plugin.c:279: error: 'icon' undeclared (first use in this function)
launcher-plugin.c:289: error: 'KIBA_DESKTOP_STATE_ACTIVE' undeclared (first use in this function)
launcher-plugin.c: In function 'launcher_active_window_changed_cb':
launcher-plugin.c:297: error: 'KibaDesktopIcon' undeclared (first use in this function)
launcher-plugin.c:297: error: 'icon' undeclared (first use in this function)
launcher-plugin.c: In function 'launcher_plugin_load':
launcher-plugin.c:382: error: 'KibaDesktopIcon' undeclared (first use in this function)
launcher-plugin.c:382: error: 'icon' undeclared (first use in this function)
launcher-plugin.c:392: error: too many arguments to function 'kiba_launcher_add'
make[3]: *** [launcher-plugin.lo] Error 1
make[3]: Leaving directory `/home/adam/kiba/kiba-plugins/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/adam/kiba/kiba-plugins/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/adam/kiba/kiba-plugins'
make: *** [all] Error 2

```

Not sure what to make of this since Kiba-dock is now running.

---

### Post by walkerk on 2007-11-18
Nice how-to... It worked on my laptop flawlessly though I did uninstall it.. not a fan of docks. I have to say kiba is much nicer than awn... though i haven't used awn in like 6 months...

---

### Post by ncappel1 on 2007-11-19
hmmm.... I tried to uninstall, then restart the howto from step one and trying it with --enable glitz, but I don't notice any difference, in fact, now I can't run it without sudo. If I try to enter kiba-dock into my terminal without sudo I get a "segmentation fault." what could be the cause of this? Where is the --enable glitz option supposed to be entered?

---

### Post by IsraeliHawk on 2007-11-20
thank you for an awesome step-by-step HOW:TO!!

you couldn't have done it any better.. 
my only question is if there's a possibility to remove the black backround behind the dock? 
It disconnects it from the rest of the screen, making my screen much smaller.
i believe it's because of my old NVIDIA card, but maybe there's some surt of solution? :)

thanks in advance!

---

### Post by Kedster on 2007-11-20
i still get the same error  
```
kedster@kedster-laptop:~$ cd kiba-dock/
kedster@kedster-laptop:~/kiba-dock$ ./autogen.sh
bash: ./autogen.sh: No such file or directory

```

---

### Post by mattgaunt on 2007-11-21
kedster could u output everythin for all of the commands that u have done to install kiba-dock

if u wanted another option these is an installation script for ubuntu - so maybe worth trying that - i think someone mentioned it earlier on in this topic

Gaunt

---

### Post by mattgaunt on 2007-11-21
IsraeliHawk im pretty sure that u need to have kiba-dock running on top compiz-fusion to get rid of the black box around

And to have compiz-fusion running u need to have an XGL or AIGLX session running

Do u have compiz-fusion on ur comp??

Gaunt

---

### Post by Mikey_W on 2007-11-21
Im also new to ubuntu and all the linux families
I keep getting this error when trying to install kiba dock or awn (well along the same lines) but only on my desktop not on my laptop and havent a clue why.. any help plz?

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
  libasound2-dev: Depends: libc6-dev but it is not going to be installed or
                           libc-dev
  libgconf2-dev: Depends: libpopt-dev but it is not going to be installed
  libglitz1-dev: Depends: xlibmesa-gl-dev but it is not going to be installed or
                          libgl-dev
  libgnome-menu-dev: Depends: libgnome-menu2 (= 2.20.0-0ubuntu1) but 2.20.1-0ubuntu1 is to be installed
  libgnomeui-dev: Depends: libgnomeui-0 (= 2.20.0-0ubuntu1) but 2.20.1.1-0ubuntu1 is to be installed
                  Depends: libgnome2-dev (>= 2.13.7) but it is not going to be installed
                  Depends: libbonoboui2-dev (>= 2.13.1) but it is not going to be installed
                  Depends: libjpeg62-dev but it is not going to be installed or
                           libjpeg-dev
  libgnomevfs2-dev: Depends: libc6-dev but it is not going to be installed
                    Depends: libgnutls-dev but it is not going to be installed
  libgstreamer-plugins-base0.10-dev: Depends: libc6-dev but it is not going to be installed or
                                              libc-dev
  libgstreamer0.10-dev: Depends: libc6-dev but it is not going to be installed or
                                 libc-dev
                        Depends: libpopt-dev but it is not going to be installed
  libgtk2.0-dev: Depends: libcairo2-dev but it is not going to be installed
  libpango1.0-dev: Depends: libpango1.0-0 (= 1.18.2-0ubuntu1) but 1.18.3-0ubuntu1 is to be installed
                   Depends: libfreetype6-dev (>= 2.1.3) but it is not going to be installed
                   Depends: libxft-dev but it is not going to be installed
                   Depends: libfontconfig1-dev (>= 2.1.91) but it is not going to be installed
                   Depends: libcairo2-dev (>= 1.2.6) but it is not going to be installed
  librsvg2-dev: Depends: libc6-dev but it is not going to be installed
                Depends: libpopt-dev but it is not going to be installed
                Depends: libgsf-1-dev (>= 1.9.1-6) but it is not going to be installed
  libsdl1.2-dev: Depends: libglu1-xorg-dev but it is not going to be installed or
                          libglu-dev
  libtool: Depends: libc6-dev but it is not going to be installed or
                    libc-dev
  libxml2-dev: Depends: zlib1g-dev but it is not going to be installed or
                        libz-dev
E: Broken packages


its this bit of code thats the bother (so far)
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev

---

### Post by mattgaunt on 2007-11-21
hey mikey_w do u have all the repo's set up properly??

I think if u look at [www.ubuntuguide.org](www.ubuntuguide.org) it has a gd guide to set - up your sources list and repo's

Gaunt

---

### Post by Kedster on 2007-11-21
if iv done it already how do i get the output for it like do i just do it again or what

---

### Post by sweetfishremix on 2007-11-21
vu@vu-laptop:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru
Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? p
svn: PROPFIND request failed on '/svnroot/kibadock/trunk/akamaru'
svn: PROPFIND of '/svnroot/kibadock/trunk/akamaru': Server certificate verification failed: issuer is not trusted ([https://kibadock.svn.sourceforge.net](https://kibadock.svn.sourceforge.net))

I got this after I accepted it pernamently....

And I typed in p, not pernamently ;D
T_

---

### Post by mattgaunt on 2007-11-22
kedster u can't get it back, i have a feeling u need to cd kiba-dock and then cd into each part of the directory to run autogen

What im trying to find out is if u ran each command and what command u got up to before having a problem.

If u jus manually search through your home folder, is kiba-dock folder there and in that are there several other folders??

sorry sweetfishremix i wouldnt know what to do for that problem - im guessin temporarily accept wont work either will it??

Gaunt

---

### Post by Kedster on 2007-11-22
i got it worken fine lol thanx its a simple error on my part i didnt relize the that after i did the first sommand ```
cd ..
``` that i had to then go in another folder (sub folder)named kiba dock i tought u were just stating ot showing that u were in the kiba dock floder so i was tryin to do every tin in the main folder lol

---

### Post by mattgaunt on 2007-11-23
lol kool kool glad u sorted it out

Gaunt

---

### Post by packoman on 2007-11-23
Hi.
I tried installing kiba-dock from SVN following the Howto. Unfortunately it doesn't work. When I launch from the console I get the following errors:

```

micha@Herbert:~$ kiba-dock 
/home/micha/.themes/T-ish-Brushed-Overlaid/gtk-2.0/gtkrc:63: Clearlooks configuration option "sunkenmenu" is not supported and will be ignored.
/home/micha/.themes/T-ish-Brushed-Overlaid/gtk-2.0/gtkrc:64: Clearlooks configuration option "menuitemstyle" is not supported and will be ignored.
/home/micha/.themes/T-ish-Brushed-Overlaid/gtk-2.0/gtkrc:65: Clearlooks configuration option "listviewitemstyle" is not supported and will be ignored.
/home/micha/.themes/T-ish-Brushed-Overlaid/gtk-2.0/gtkrc:136: Background image options specified without filename
*** stack smashing detected ***: kiba-dock terminated
Aborted (core dumped)

```

It also appears shortly at the bottom of the screen and then disappears again. I have the feeling that it has to do with kiba-dock not finding some (most?) of its icons, because when I go into the kiba-dock Settings Editor, I get the following error window when selecting the objects-tab:

'The folder content could not be displayed.
error accessing 'file:///usr/share/kiba-dock/icons': File not found"

I checked on the console and the folder /usr/share/kiba-dock/icons doesn't exist. kiba-dock was installed into /usr/local/share/kiba-dock . Just for the heck of it I copied the kiba-dock folder also to  /usr/share/ and now I don't get the error winow in kiba-dock settings anymore, but the first problem still persists. It seems as if the installation configuration wasn't correct. So I suppose I'll have to adapt that(?).
Any help on what might be wrong and how to solve it, will be greatly appreciated.
Thanks in advance,
Michael

---

### Post by mattgaunt on 2007-11-24
Michael if i cud help i would but i honestly wouldnt know where to start, all i can suggest is putting a post on the kiba-dock forum or try searching the forum for someone with similar if not same problem.

Im bit lost as to why kiba-dock is trying to find things in the folder /home/micha/.themes/T-ish-Brushed-Overlaid/

Since the how-to should of put everything in /home/micha/kiba-dock

Sorry dude

Gaunt

---

### Post by rune0077 on 2007-11-25
I've had Kiba-dock installed for a while now. Does anyone know how to easily update it (in case there are new versions of the plugins and such)? Is there a command to do this or do I have to completely reinstall the whole darn mess?

---

### Post by piratesmack on 2007-11-25
You can put down that this works in Linux Mint

---

### Post by mattgaunt on 2007-11-26
rune i hav a feeling its jus svn up when ur in the kiba-dock directory but im not a hundred percent sure

if u google it or look on the kiba-dock forums u should hopefully find sumtin

Let me kno how it goes

Gaunt

---

### Post by ncappel1 on 2007-11-26
rune, I visited the kiba-dock site and found this thread on their forums, I don't know if the script works, as I havn't tried it, but it may be helpful. if you run it, let us know how it works out: [http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=274.0](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=274.0)

---

### Post by IsraeliHawk on 2007-11-26
> **mattgaunt said:**
> IsraeliHawk im pretty sure that u need to have kiba-dock running on top compiz-fusion to get rid of the black box around

And to have compiz-fusion running u need to have an XGL or AIGLX session running

Do u have compiz-fusion on ur comp??

Gaunt

:/ no i don't .. the system tells me that i can't run Deffects with it :(

i believe that's the main reason - i thought you might enlight me with a brand new solution .. :lolflag:

---

### Post by rune0077 on 2007-11-26
> **mattgaunt said:**
> rune i hav a feeling its jus svn up when ur in the kiba-dock directory but im not a hundred percent sure

if u google it or look on the kiba-dock forums u should hopefully find sumtin

Let me kno how it goes

Gaunt

When I run svn up kiba-dock I just get this: Skipped 'kiba-dock'. Dunno what that means though.

The script didn't do anything either (I think you need to use it to install kiba-dock before you can use it to update it).

---

### Post by mattgaunt on 2007-11-26
yeah do jus need to change directory into each sub folder of kiba-dock and jus type svn up

[http://www.kiba-dock.org/](http://www.kiba-dock.org/) - look on wiki - how to install

Ill try writing a lil how - to later on

Gaunt

---

### Post by Six_Digits on 2007-11-27
Worked great for me, awesome first-time how to!

---

### Post by rune0077 on 2007-11-27
> **mattgaunt said:**
> yeah do jus need to change directory into each sub folder of kiba-dock and jus type svn up

[http://www.kiba-dock.org/](http://www.kiba-dock.org/) - look on wiki - how to install

Ill try writing a lil how - to later on

Gaunt

Oh okay, I figured it out. Thanks alot.

---

### Post by BLTicklemonster on 2007-11-28
I followed up until the second part in akamaru, then got this:

checking for AKAMARU... configure: error: Package requirements ("glib-2.0 >= 2.8.0 gobject-2.0") were not met:

No package 'glib-2.0' found
No package 'gobject-2.0' found


I've been sitting here for over an hour trying to get kiba dock installed before I found this thread. Quite frankly, I'm a bit tired of ./configuring ever file under the sun just to end up at a brick wall again.

There's not a deb for this baby is there?

Supposing there's not, I went and got the newest glib I could find. 2.0.7

Requested 'glib-2.0 >= 2.8.0' but version of GLib is 2.0.7 

is what I'm told. Now correct me if I'm wrong, but isn't 2.0.7 between 2.0 and 2.8?

Jeez.

(I also downloaded 2.0.0 and get Requested 'glib-2.0 >= 2.8.0' but version of GLib is 2.0.0)

now what?

---

### Post by mattgaunt on 2007-11-28
Hey ticklemonster

one question - have you installed the glib2.0-dev dependencie as well??

also i have version 2.14.1 of glib2.0-0 installed from synaptic so maybe u shud re-install glib from synaptic as well as the -dev depency

Gaunt

---

### Post by BLTicklemonster on 2007-11-28
Well, X won't start at all any more.

But, I have gutsy on two drives, so I can boot to the other one which already had kiba on it (which is odd, I apparently COULD install it at one time, but can't now. Which is "ubuntu in a nutshell" if you ask me)

So I checked it out, and now I remember a problem I had with it that showed up in Gnome and IceWM.

[[IMG]http://img508.imageshack.us/img508/9413/screenshotlm5.th.png[/IMG]](http://img508.imageshack.us/my.php?image=screenshotlm5.png)

click that and look at the dock at the bottom. I can't shake that black border, and I got spider web looking thingies at the bottom of some of my icons, plus, some of the icons just up and float away when I click on them.

Any ideas what to do?

And yes, that's kiba, not awn.

---

### Post by mattgaunt on 2007-11-28
cant help with the spider web thing i had that when i installed it

As for the black border, normally this is cause when someone is runnin kiba-dock and not running compiz-fusion

Are you running compiz-fusion??

Gaunt

---

### Post by BLTicklemonster on 2007-11-28
Hmmm, I'll look and see when I get home. So can you even run compiz stuff at all in icewm or flux box? That pic is from gnome, but I run icewm a lot.

---

### Post by mattgaunt on 2007-11-28
to be honest ive never even heard of icewm - i think compix works with fluxbox

Best bet is just to drop a post at forum.compiz-fusion.org really friendly forum and sure someone will be able to help you out with that side of things

Gaunt

---

### Post by Depressed Man on 2007-11-28
The spider crack thing only happens on programs in the taskbar oddly.. so it's some sort of notification..

---

### Post by rune0077 on 2007-11-28
> **Depressed Man said:**
> The spider crack thing only happens on programs in the taskbar oddly.. so it's some sort of notification..

It's just to indicate what programs you've got running. You can turn it off in the settings (the "Triangle" tab under Objects) or pick a new image to show if you don't like the "spider crack thing" (it's supposed to be brocken glass, according to the name of the file used to display it :))

---

### Post by BLTicklemonster on 2007-11-28
Compiz fusion is running now, and kiba is working right. Thanks!
Now I wonder what happened to my other ubuntu lol.

---

### Post by packoman on 2007-11-29
Hi.
Well I solved the problem with the stack smashing. Turns out I didn't have a package installed that was needed for setting up the compilation and install process correctly. That's why it didn't install correctly. Unfortunately I can't remember what package it was.
So for anyone who gets that error check that you installed all dependencies required.
Cheers,
Michael

---

### Post by BLTicklemonster on 2007-11-29
Wow, here's a great little script for intalling kiba dock if you would rather go that route:

[http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.msg2740](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&topic=540.msg2740)

---

### Post by jstableford on 2007-11-29
Awesome, worked like a charm, although I had to add the 'make' command between config-sh and make install...

Thanks for the hot tip!

Jason

---

### Post by BLTicklemonster on 2007-11-30
One difference though. I don't get the same effects from this one as I did from an earlier install before.

I looked over the script, and the only real difference I see is in the very beginning where you install the dependencies. This thread's instructions include 

pidgin-dev libpurple-dev

whereas the script I posted to doesn't. pidgin-dev of course is for pidgin, but would libpurple-dev perhaps be the difference, I wonder? I really liked the icons bouncing up in the air (not the physics setting, just the mouse-over bounce) of the other. And the smooth curve I could get with the dock in the older looked better than this one.

Oh, and dang, I'm on a laptop with an ati card, and compiz doesn't work. I think it's ati mobility drivers or something. I need to find out what to add to xorg.conf to get compiz to work. Time to google advance, lol.

---

### Post by solinent on 2007-11-30
I'm getting this error, (I assume this is just because it is svn, and if I wait a couple days it'll be fixed?)
 (with kiba-plugins)
launcher.c:41:27: error: kiba-key-file.h: No such file or directory

Then it exits.  I did compile it before, but the aforementioned plugins were not working, nor were the dbus (or it was erratic).  I saw some people fixed this by re-compiling (must have been fixed in svn).

Maybe I should look for trevino's repoistory?

---

### Post by mattgaunt on 2007-11-30
trevino's repo's are definately an easier way of gettin kiba-dock but he does use bleeding edge software

If he updates and the update doesnt work - then your a bit stuck

So definately use it jus bare that in mind - this method just mean when it works u can stick with it is all

Gaunt

---

### Post by flaw3d on 2007-12-01
as it is with quite a few others im a complete noob to linux. ive tried this several times now and every time it fails on the 2nd command with the message 

"Package automake1.9 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package automake1.9 has no installation candidate"

now from what i understand that means automake1.9 isnt findable?

really have no clue on what to do and it doesnt seem anyone else has had this problem!

---

### Post by flaw3d on 2007-12-01
my bad, sorted, hadnt set the universe thing! :P thanks anyway

---

### Post by jordanae on 2007-12-02
everything is fine up until i get to the 32 bit part. any help?

---

### Post by mattgaunt on 2007-12-02
jordane what happens when u try the 32-bit part???

Copy and paste the output from your terminal to here so people can see the error

Gaunt

---

### Post by Levo75 on 2007-12-02
Thank You Very Much Kind Sir.

You Win Many Internets.

---

### Post by linux4909 on 2007-12-02
> linux4909@LPT4909:~/kiba-dock/akamaru$ ./autogen.sh --prefix=/usr --exec-prefix=/usr

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.in: 28: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: aclocal failed with exit status: 1
linux4909@LPT4909:~/kiba-dock/akamaru$ 

i get this far. i dont know what is causing this error message. 
anyone have any ideas?

---

### Post by jordanae on 2007-12-02
jordan@HP-Pavilion:~/kiba-dock$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru

Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? svn: PROPFIND request failed on '/svnroot/kibadock/trunk/akamaru'
svn: PROPFIND of '/svnroot/kibadock/trunk/akamaru': Server certificate verification failed: issuer is not trusted ([https://kibadock.svn.sourceforge.net](https://kibadock.svn.sourceforge.net))


I keep on getting that error message. Any help?

---

### Post by mattgaunt on 2007-12-03
At this point

(R)eject, accept (t)emporarily or accept (p)ermanently?

You should just be able to type

p

and it should work - i can't remember if there was another way around for some other users

Gaunt

---

### Post by sweetfishremix on 2007-12-05
Still no clue for the Permanently accepting Issue? I still have the same problem T_T

:Edit:
Ok I got it installed. To Bypass the Accepting problem by adding the code One line at a time. 

1.mkdir kiba-dock
2.cd kiba-dock
Then each one at a time
1.svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru
2.svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/) kiba-dock
3.svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/) kiba-plugins
4.svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/) kiba-dbus-plugins

But now I have a new problem. My akamaru gravity engine is acting werid....It's hard to explain but the icons do not fall in place properly......And they fly around randomly....I tryed setting the settings at default but they still act really werid....Any solutions?

---

### Post by Christian Christiansen on 2007-12-05
When I type in kiba-dock it comes up with 
Error (main.c @ line 252):
        Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-path' command line parameter.

When I looked for /usr/local/lib/kiba-dock it wasn't there.
What do I do?

---

### Post by sweetfishremix on 2007-12-05
it should just be located within your user accont. And try reinstalling the plugins.

---

### Post by Christian Christiansen on 2007-12-06
I managed to get it working :) by copying some files into /usr/local/lib/kiba-dock. But now when I open kiba-dock all it does is come up with a triangle at the bottom. I've tried dragging things on but it doesn't work. What do I need to do?

---

### Post by santiagoward2000 on 2007-12-11
Hi!
I have a question about a Kiba option. If I enable **Grouping** for **Launchers**, is there any way I can choose which icon stays on top when I start kiba?

---

### Post by boast on 2007-12-14
I don't know if this has been asked,but what from ```
libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
```
can be removed after compiling?
(when I first used linux I would compile everything, so I would have 20gb worth of dev's and other files)

---

### Post by exactopposite on 2007-12-16
> **exactopposite said:**
> thanks a lot for this. i followed the howto  and it's working fine in 32bit gutsy.

for the record i had to remove it becasue it wasnt' stable at all for me. i installed awn and awn is A LOT more stable on my system. i'm not sure why, but that's how it worked out for me. 

(i also switched to 64bit but that was after i ditched kiba)

---

### Post by spacedude1111 on 2007-12-21
Thanks but when i do this:
_________________________________________________________
Then make the directory to install kiba-dock into

Code:

mkdir kiba-dock
cd kiba-dock
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/) kiba-dock
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/) kiba-plugins
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/) kiba-dbus-plugins
_________________________________________________________

i get this message:

Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? p
svn: PROPFIND request failed on '/svnroot/kibadock/trunk/akamaru'
svn: PROPFIND of '/svnroot/kibadock/trunk/akamaru': Server certificate verification failed: issuer is not trusted ([https://kibadock.svn.sourceforge.net](https://kibadock.svn.sourceforge.net))
ethan@ethan-laptop:~/kiba-dock/kiba-dock/kiba-dock$ 
________________________________________________________

What do i do? Im still new to Ubuntu so i kinda need help.

---

### Post by dr_drea on 2007-12-22
same problem over here. Seems like its global :P

---

### Post by mattgaunt on 2007-12-23
I think one of the users said i fix was to make the folders for each thing and then try the svn command

mkdir akamaru

svn . . . . 

I think if you look over this thread someone solved it

Hope that helps a little

Gaunt

---

### Post by Loki1989 on 2007-12-27
I have wanted kiba dock since I saw it on youtube quite a while back now I have it on my laptop and watch out desktop here I come...

edit 
just copy paste all of them seperately it worked for me.

---

### Post by pelo8280 on 2008-01-01
After I installed it I just got a bunch of white boxes for the Taskbar.  Also, my settings aren't saved when I close it and reopen kiba dock.

---

### Post by einheitlix on 2008-01-02
> **Faud said:**
> Got it figured out. 
Woot

:)

First you complain about not finding any solution on the net, then you solve it yourself, and you don't deem necessary to tell the community how... nice :evil:

I had that very same problem too on my Ubuntu machine and managed to solve it, so should anyone else encounter this problem and google for it looking for a solution, here's what did the trick for me:

```
sudo apt-get install automake1.9
```

...as simple as that :)

[edit]
PS. Since I just noticed that post was some pages earlier in this thread, the problem was this:

> 
# ./autogen.sh 

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
autoreconf: `aclocal.m4' is unchanged
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy
Putting files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy
libakamaru_la_LDFLAGS: variable `export_symbols' is used but `export_symbols' is undefined
autoreconf: automake failed with exit status: 1


...when trying to compile akamaru manually from the kiba svn version.

---

### Post by Fleece Flamingo on 2008-01-03
> **spacedude1111 said:**
> Thanks but when i do this:
_________________________________________________________
Then make the directory to install kiba-dock into

Code:

mkdir kiba-dock
cd kiba-dock
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/) kiba-dock
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/) kiba-plugins
svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/) kiba-dbus-plugins
_________________________________________________________

i get this message:

Error validating server certificate for 'https://kibadock.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? p
svn: PROPFIND request failed on '/svnroot/kibadock/trunk/akamaru'
svn: PROPFIND of '/svnroot/kibadock/trunk/akamaru': Server certificate verification failed: issuer is not trusted ([https://kibadock.svn.sourceforge.net](https://kibadock.svn.sourceforge.net))
ethan@ethan-laptop:~/kiba-dock/kiba-dock/kiba-dock$ 
________________________________________________________

What do i do? Im still new to Ubuntu so i kinda need help.
Copy paste each one individually.

---

### Post by mattgaunt on 2008-01-03
I updated the how-to so the problem regarding the svn being entered all in one go is in seperate chunks

Cheers for giving me the solution guys - Hopefully no-one will make the mistake anymore

Gaunt

---

### Post by etm124 on 2008-01-03
hello all.

when executing this command

```
./autogen.sh --prefix=/usr --exec-prefix=/usr
```

i get this error:

```

edwin@laptop:~/kiba-dock/akamaru$ ./autogen.sh --prefix=/usr --exec-prefix=/us

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.in: 28: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: aclocal failed with exit status: 1


```

thank you for your help.

---

### Post by etm124 on 2008-01-03
```
sudo aptitude install libgconf2-d
```

will fix the above problem.

now i get this. 

```
libakamaru_la_LDFLAGS: variable `export_symbols' is used but `export_symbols' is undefined
src/Makefile.am: installing `config/depcomp'
autoreconf: automake failed with exit status: 1

```

i'll dig some more...

---

### Post by -gabe-noob- on 2008-01-04
gabe@gabe-laptop:~$ sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev
[sudo] password for gabe:
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


I'm having problems down the line but I read that you have to have auto make 1.9 to fix it and when I try the code you said to get it the last two lines of the out put make me think that I screwed up somehow

---

### Post by war59312 on 2008-01-05
Excellent guide, worked perfectly the very first time. :)

---

### Post by pikitsan on 2008-01-05
Hi,should i have Beryl/compiz to enable the dock ???I installed it but there is a line in the dock it's not transparent....Can anyone help me ???Here is a [screenshot]("http://img232.imageshack.us/img232/3994/screenshotzo0.png") of the problem....


[[IMG]http://img232.imageshack.us/img232/3994/screenshotzo0.th.png[/IMG]](http://img232.imageshack.us/my.php?image=screenshotzo0.png)

---

### Post by mattgaunt on 2008-01-05
Yeah u need beryl / compiz running to use kiba-dock

-gabe-noob- -> I think that is a bug in gutsy gibbon, its nothing to do with the packages, its jus ubuntu not being able to get to synaptic package manager - can u still everything else u hav tried using sudo apt-get *Random program*

Gaunt

---

### Post by pikitsan on 2008-01-05
Can anyone suggest me a dock for gnome that not want beryl/compiz ???I have ubuntu 7.04.

---

### Post by Fleece Flamingo on 2008-01-06
Uninstall doesnt work for me!

---

### Post by lolzlolz on 2008-01-06
no wonder kiba-dock won't run my gfx card doesnt support xgl....

---

### Post by Phil420 on 2008-01-07
is it normal that when i type the code it does this?

```

cd akamaru/ &&
>./autogen.sh --prefix=/usr --exec-prefix=/usr --libdir=/usr/lib64 &&
>sudo make install &&
>cd .. &&

```

it only does ">" things and at the end, after coding for so long, it says no such file directory or something... what am i doing wrong?

---

### Post by Phil420 on 2008-01-07
okay never mind the last post...
emm when i try to "sudo make install" for kiba-dock it says:

```

make: *** No rule to make target 'install'. Stop.

```

whaaaaaaaaaaaaaaat????
thanks :P

---

### Post by robokiller on 2008-01-08
You bloody legend mate.. awesome how-to.. very simple and i love the 64bit section. :)

---

### Post by robokiller on 2008-01-08
> **Phil420 said:**
> okay never mind the last post...
emm when i try to "sudo make install" for kiba-dock it says:

```

make: *** No rule to make target 'install'. Stop.

```

whaaaaaaaaaaaaaaat????
thanks :P

do "sudo make" then "sudo make install"

---

### Post by ravenon on 2008-01-08
I am trying to build this on a 64 bit Gutsy. All works well save the plugin stuff

The command
CC="gcc -fPIC" ./autogen.sh --prefix=/usr --libdir=/usr/lib64 

while in the kiba-plugin folder gives an error because of the CC=  stuff

and running ./autogen.sh  etc without works however then make fails with the comment to recompile with the -fPIC option.

How does one make this work?

---

### Post by Phil420 on 2008-01-08
thank you very much for this howto it was difficult but i came through after all. one last thing though, when i write kiba-dock in the terminal, it says
```

kphil@Phil-Desktop:~$ kiba-dock

** (kiba-dock:27542): WARNING **: Error (plugin.c @ line 205):
        '/usr/local/lib/kiba-dock/libdbus.so' is not loadable

```

and when i close the terminal, it closes with it. i tried with alt+f2 and i could enable it, but i still have problem with the plugins some things don't work. does anyone know what to do?
thanks!

---

### Post by mattgaunt on 2008-01-09
Hey guys, if there is anything on the 64-bit section of the how-to i should change please let me kno and ill edit it

Thanks alot

Gaunt

---

### Post by ravenon on 2008-01-09
This is the error I am getting following the howto on a 64 bit while building the plugins.

[CODE][/usr/bin/ld: ./.libs/liblauncher-type.a(launcher.o): relocation R_X86_64_32 against `a local symbol' can not be used when making a shared object; recompile with -fPIC
./.libs/liblauncher-type.a(launcher.o): could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [liblauncher.la] Error 1
make[2]: Leaving directory `/home/merlin/Desktop/kiba-dock/kiba-plugins/src'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/merlin/Desktop/kiba-dock/kiba-plugins/src'
make: *** [install-recursive] Error 1]

Any thoughts on how to fix?

---

### Post by mattgaunt on 2008-01-09
have u tried compiling it with -fPIC???

But otherwise im not too sure how to fix it, only thing i can suggest is asking arnd on the kiba-dock forums

Gaunt

---

### Post by giok13 on 2008-01-13
hey i get this error 

sudo kiba-dock
kiba-dock: error while loading shared libraries: libakamaru.so.0: cannot open shared object file: No such file or directory

---

### Post by pelo8280 on 2008-01-13
When I run kiba-dock, I just get white boxes.  Also, settings aren't saved.

---

### Post by z-bot on 2008-01-14
Hi, thanks for taking the time to produce such good quality tutorial.  One quick note though, I tried adding the Feisty repositories to my apt sources, and I was able to get the kiba-dock working with a simple apt-get install kiba-dock. 

I don't know if I'll run into much trouble by doing this, but so far so good.  I just wanted to share that with ya'll, especially since this is very viable for newbies trying to find easier solutions (assuming my approach works for them).

Cheers,
-z-bot

---

### Post by mattgaunt on 2008-01-15
The only thing with that is the svn is more up to date where as the apt-get you will be relyin on someone else to do a gd job at packagine and keep repo up to date.

But you are right that it is definately a more preferable method for alot of people

Gaunt

---

### Post by zeusalmighty on 2008-01-18
Is there any way to correctly use the Tray with kiba-dock? Also, can I remove all panels from my desktop? No matter what I do, always one remains...

---

### Post by HeresJohnny on 2008-01-22
Hey, wow.  Worked first time and now I'm rocking the kiba-dock!  Thanks, my friend, for a job well done.  I totally have a man-crush on you now.  :guitar:

---

### Post by SomeGuyDude on 2008-01-23
> **zeusalmighty said:**
> Is there any way to correctly use the Tray with kiba-dock? Also, can I remove all panels from my desktop? No matter what I do, always one remains...

What I do is go into "properties", then uncheck "expand", drag the whole thing to the right. Afterwards, go back into "properties" and select "show hide buttons" but uncheck "arrows on hide buttons". That way you can hide the thing to the corner save a small sliver and then take it back when you need it.

For some reason, GNOME's "autohide" feature for the panels absolutely sucks, as it doesn't "hide", it just shrinks down thinner. On KDE the panel DISAPPEARS when you autohide it and works great for that kinda thing. Here there's literally no way to make the panels invisible.

---

### Post by Ryadt on 2008-01-23
hi...when I type this command :./autogen.sh
I just get this message

checking for DBUS... configure: error: Package requirements (dbus-glib-1) were not met:

No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

r@ubuntu:~/kiba-dock/kiba-dock$ sudo make install 
make: *** No rule to make target `install'. Stop.
r@ubuntu:~/kiba-dock/kiba-dock$ 


can someone please help
thx

---

### Post by xfearxnxloathing on 2008-01-24
> **SomeGuyDude said:**
> What I do is go into "properties", then uncheck "expand", drag the whole thing to the right. Afterwards, go back into "properties" and select "show hide buttons" but uncheck "arrows on hide buttons". That way you can hide the thing to the corner save a small sliver and then take it back when you need it.

For some reason, GNOME's "autohide" feature for the panels absolutely sucks, as it doesn't "hide", it just shrinks down thinner. On KDE the panel DISAPPEARS when you autohide it and works great for that kinda thing. Here there's literally no way to make the panels invisible.


hold alt + mousewheel down untill the transparency is at its lowest then rightclick panel and check autohide, practically invisible! :)

---

### Post by mattgaunt on 2008-01-24
> **Ryadt said:**
> hi...when I type this command :./autogen.sh
I just get this message

checking for DBUS... configure: error: Package requirements (dbus-glib-1) were not met:

No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DBUS_CFLAGS
and DBUS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

r@ubuntu:~/kiba-dock/kiba-dock$ sudo make install 
make: *** No rule to make target `install'. Stop.
r@ubuntu:~/kiba-dock/kiba-dock$ 


can someone please help
thx

Try searchin for dbus-glib-1 in synaptic and install it and install and with -dev at the end of it

Hope that works

Gaunt

---

### Post by Vivica_Gsy on 2008-01-24
I have one issue...

I have created a Firefox launcher, which like most people (i presume) brings up an error because its directed to "firefox 0", and obviously there's no page at [http://0](http://0).
I did the logical thing and edited the launcher to simply be directed at "firefox".

This now works well and i'm directed to my home page when Firefox opens, which is fantastic.
But the problem now is that as well as the Firefox launcher itself, i'm now presented with **TWO** aditional Firefox logo's on the dock... WHY?

Brilliant little walk through though, very good indeed.

---

### Post by mattgaunt on 2008-01-25
unfortunately alot of the problems on here are to do with the kiba-dock programming, unfortunately its not the most stable dock available.

Gaunt

---

### Post by mab1376 on 2008-01-26
```
mark@mark-laptop:~/kiba-dock/kiba-dbus-plugins$ sudo make uninstall
make: *** No rule to make target `uninstall'.  Stop.
mark@mark-laptop:~/kiba-dock/kiba-dbus-plugins$ 
```

?? why is it doing that?

---

### Post by mattgaunt on 2008-01-27
Dont you wanna type 'install' not 'uninstall' ???

Gaunt

---

### Post by 4seasonphotos on 2008-01-28
Hi I yesterday installed Kiba Dock but I see no trace of it. I followed all your instructions Matt.  When I did the last thing type in kiba-dock.. It said.. Segmentation fault (core dumped) I am not real familiar with Ubuntu but I don't think that sounds good. 

I do see kiba dock settings icon and kiba-dock icon in accessories..  

How do I actually start the program?  Or see if I have it installed correctly? 

Thanks in advance!

---

### Post by mattgaunt on 2008-01-29
unfortunately it snds like u didnt install it correctly, when u went through the howto, did any errors come up??

Gaunt

---

### Post by 4seasonphotos on 2008-01-29
Hi Matt, 

 I did everything 3x's to make sure I did it right and I see no errors.. I did not do the 32bit section nor the section pertaining to gaim.  I see no errors. It is only when I type in the last command is when I see segment dump core. I have the script install of Kiba dock I can paste it somewhere for you so you can check it out if you want I just don't want to paste it here it is too large. 

If it is installed correctly what do I do to start the actual program?

Thanks

---

### Post by startherepodcast on 2008-01-29
Great tutorial.. Got Kiba - Dock up and running in a few minutes!

But there was one thing that annoyed me: The volume plugin was missing. So here is how to get the Volume plugin; It's cool: You can hover over it and regulate the volume with the scroll wheel! This fix had the nice side effect that no there is the system monitor too..

1. Assuming that you already have everything installed, navigate to the kiba-plugins directory. If you did everything exactly the way it said in the tutorial, open up a new terminal and type:
```
cd ./kiba-dock/kiba-plugins
```

2. Now lets recompile all the plugins; It would hang for me if I simply used "make", so I had to use "sudo make"
```
sudo make
```

3. Now that everything compiled, lets put all the newly generated files in place:
```
sudo make install
```

4. Fire up Kiba-Settings and enjoy your new plugins!


Hope that helped some people!

Leon

---

### Post by mattgaunt on 2008-01-29
4seasonphotos best thing to do is to g oto kiba-docks forum and post ur problem there, someone there will have a much greater understanding of how kiba-dock works and will help you out, im afraid i cant sorry

Gaunt

---

### Post by team_milan on 2008-01-30
i had the exact same problem as 4season. one thing i did find was when the autogen step for the dbus plugins i got something looking like:

Running libtoolize, please ignore non-fatal messages....
Remember to add `AC_PROG_LIBTOOL' to `configure.ac'.
You should update your `aclocal.m4' by running aclocal.

You should update your 'aclocal.m4' by running aclocal.
Running ./configure --prefix=/usr --libdir=/usr/lib64

but the installer kept on going and completed all the steps without a hitch.
i think i might have got something along the same lines in some of the other steps but it moved far too fast for me to tell.

im fairly new to linux as well but the forums make it (relatively) easy to make it seem like im a pro at it. if that output helps you help me at all that would be great, if not, thanks anyway for all the help already

---

### Post by mattgaunt on 2008-01-30
team_milan did u solve this problem or not??

Im assuming u ran aclocal in a terminal to fix that problem??

Gaunt

---

### Post by team_milan on 2008-01-30
no, i actually have no idea what aclocal is, or how to use it or anything, i was hoping you could explain it to me.

---

### Post by mattgaunt on 2008-01-30
unfortunately i have no idea wot it is either, but im all about trial and error, so try typing in aclocal in a terminaland see if it solves ur problems.

Unfortunately i only wrote the guide using what worked for me, if something goes wrong i dont really kno wot to do i can only try and help, most times it is just a matter of a depency not being installed, this is different i reckon.

Gaunt

---

### Post by team_milan on 2008-01-30
thanks, ill try it out then.

---

### Post by twistadias on 2008-01-30
im getting the following error

```
croydon@croydon-tablet:~/kiba-dock/akamaru$ ./autogen.sh --prefix=/usr --exec-prefix=/usr

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.in: 28: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: aclocal failed with exit status: 1



```

Someone suggested to install automake 1.9, after which I got this error

```

croydon@croydon-tablet:~/kiba-dock/akamaru$ ./autogen.sh --prefix=/usr --exec-prefix=/usr

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
aclocal:configure.in:28: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: configure.in: tracing
autoreconf: configure.in: creating directory config
autoreconf: running: libtoolize --copy
Putting files in AC_CONFIG_AUX_DIR, `config'.
aclocal:configure.in:28: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: running: /usr/bin/autoconf
configure.in:28: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1

```

Thanks in advance

---

### Post by twistadias on 2008-01-30
Found an easier method from  [http://www.kiba-dock.org/](http://www.kiba-dock.org/)

Download this file  [Click Here](http://www.kiba-dock.org/index.php?option=com_smf&Itemid=30&action=dlattach;topic=540.0;attach=196)

Extract the file to your desktop 
then open up the terminal,

the bit of the left of the terminal tells you where you are, ie " josh@josh-computer: ~$ " means logged in as josh, on josh-computer at directory ~ (which is your home directory)

then type:
cd Desktop
which changes to your Desktop directory (capitals do matter)

then now you are in the right directory where the script is
now type
chmod +x intall_kiba-dock-en.sh
(which make it executable)
(due to a typo it is intall rather than install)
./intall_kiba-dock-en.sh i
(due to a typo it is intall rather than install)
then wait and follow the on screen instructions,
when its done, go into your main menu>accessories>kiba-dock

Please post this as an alternative on the first post. Saves us all from browsing a 30 page thread. Author says that its specially made for ubuntu

---

### Post by jellygoeswobble on 2008-01-31
You, my friend, are a hero! Ive been spending the last week trying to find out how to compile and install this whole thing and nowhere i could find had clear instructions. Thankyou so much!!

---

### Post by ashmew2 on 2008-02-01
Got it working at last !! Thanks for the uber cool HOWTO :D I didnt see that this single installation script could do the job first :P But i dont have any regrets.. But for those of you who get an error when compiling the kiba-dock :

```
/usr/include/dbus-1.0/dbus/dbus.h:30:2: error: #error "Please define DBUS_API_SUBJECT_TO_CHANGE to acknowledge your understanding that D-Bus hasn't reached 1.0 and is subject to protocol and API churn. See the README for a full explanation."
```

Just do the following : 
```

sudo gedit /usr/include/dbus-1.0/dbus/dbus.h
```

And add this line :

```

#define DBUS_API_SUBJECT_TO_CHANGE
```

Just above  : 

```
#ifndef DBUS_API_SUBJECT_TO_CHANGE
#error "Please define DBUS_API_SUBJECT_TO_CHANGE to acknowledge your understanding that D-Bus hasn't reached 1.0 and is subject to protocol and API churn. See the README for a full explanation."
#endif
```

And again try to compile it. Hope I could be of help.

---

### Post by kiikkuja on 2008-02-01
I just used your howto to install the kiba-dock and it worked flawlessly.

BTW i'm using 64-bit Gutsy and still the damn thing works!! I really hope that they keep developing this 
thing!!

---

### Post by 4seasonphotos on 2008-02-01
How exactly did you install the scripts? All I did was copy and past in terminals as the scripts were. And it did not work for me.  I must be missing something but the install process did not say anything was missing.

---

### Post by sdlvx on 2008-02-01
this worked, on kubuntu x64.  I've been trying SO HARD to get this to work.  Scouring the internets all over to find out what the problem is.  

Your howto worked, I love you, mystery internet person who write tutorials.  You have my gratitude.

---

### Post by mattgaunt on 2008-02-02
4seasonphotos, i think alot of these installation scripts are basically the same as my how-to, in the sense that it just gets the svn stuff and compiles it for you, but the script will not work if you dont have all the dependcies.

For more help on how to use the scripts go to kiba docks website and have a look on the forum,  im reluctant to put the scripts on my how-to because and havent tried them.

Gaunt

---

### Post by EnlistedSquire on 2008-02-02
Hi,

I've got this dock installed and working fairly easily thanks to this guide but can someone tell me, in the name of all that's holy and good, how you enable physics?

I've spent an hour scouring the web for some information and every forum post, blog and article I've found is talking about enabling physics but no where can I find how!

This leads me to suspect that either it's glaringly obvious but I've lost the power of sight and can't see it or my installation is somehow missing it.

FWIW, I didn't get any errors during installation.

Thanks.

---

### Post by santiagoward2000 on 2008-02-02
> **EnlistedSquire said:**
> Hi,

I've got this dock installed and working fairly easily thanks to this guide but can someone tell me, in the name of all that's holy and good, how you enable physics?

I've spent an hour scouring the web for some information and every forum post, blog and article I've found is talking about enabling physics but no where can I find how!

This leads me to suspect that either it's glaringly obvious but I've lost the power of sight and can't see it or my installation is somehow missing it.

FWIW, I didn't get any errors during installation.

Thanks.

I have this same problem here! Today I formatted my computer, and when I installed kiba-dock, I tried to enable **akamaru** but I didn't have the option. Besides, when I try to launch a program (which I had set as a launcher), that program opens on the taskbar, and the **Skip launcher** option isn't there either.
I guess there might be something wrong with the lastest SVN. Perhaps a new version will come out soon and fix these problems (I wish this is soon!)
Cheers!

---

### Post by EnlistedSquire on 2008-02-03
> **santiagoward2000 said:**
> I have this same problem here! Today I formatted my computer, and when I installed kiba-dock, I tried to enable **akamaru** but I didn't have the option. Besides, when I try to launch a program (which I had set as a launcher), that program opens on the taskbar, and the **Skip launcher** option isn't there either.
I guess there might be something wrong with the lastest SVN. Perhaps a new version will come out soon and fix these problems (I wish this is soon!)
Cheers!

Thanks, I'm relieved it's not just me. I was beginning to fear for my sanity!

---

### Post by EnlistedSquire on 2008-02-03
This was posted today on the Kiba Dock site forum:

> akamaru was broken again here, i dont have time to fix it, so i temporary removed it.
i also dont like the way it was implemented, i guess i will try to reimplement it as plugin some day, pleas be patient until then, or code it by urself 

So there you have it.

---

### Post by rabbot on 2008-02-03
ali@ali-laptop:~/kiba-dock$ kiba-dock

** (kiba-dock:7826): WARNING **: Error (main.c @ line 252):
        Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-path' command line parameter.

:(

Help?

---

### Post by Vadi on 2008-02-03
Thanks, this guide worked.

---

### Post by mattgaunt on 2008-02-04
rabbot did u get any messages come up during the process of the how-to??

Gaunt

---

### Post by intense.ego on 2008-02-04
Help! While using this command:
```
svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/ kiba-plugins
```
I got this error message
```

svn: PROPFIND request failed on '/svnroot/kibadock/trunk/kiba-plugins'
svn: PROPFIND of '/svnroot/kibadock/trunk/kiba-plugins': Could not resolve hostname `kibadock.svn.sourceforge.net': No address associated with hostname (https://kibadock.svn.sourceforge.net)
```

EDIT: Whoops! I just tried that command again and it worked,

---

### Post by intense.ego on 2008-02-04
I seem to have a problem after installing, When I try to start kiba-dock I get this message:
```
** Message: cant load file '/home/ashu/.kiba-dock/config': Failed to open file '/home/ashu/.kiba-dock/config': No such file or directory
Segmentation fault (core dumped)
```
However, if I use ```
kiba-dock &] it works.
Perhaps it has to do with this last part of the installation process:
[CODE]Generating configuration files for kiba-dbus-plugins, please wait....

Running libtoolize, please ignore non-fatal messages....
Remember to add `AC_PROG_LIBTOOL' to `configure.ac'.
You should add the contents of `/usr/share/aclocal/libtool.m4' to `aclocal.m4'.

You should add the contents of '/usr/share/aclocal/intltool.m4' to 'aclocal.m4'.
configure.ac: installing `./install-sh'
configure.ac: installing `./missing'
Running ./configure 

checking whether to enable maintainer-specific portions of Makefiles... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... none
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) none
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for intltool >= 0.35.0... 0.36.2 found
checking for perl... /usr/bin/perl
checking for XML::Parser... ok
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for PYGTK... yes
checking for KIBA_DOCK... yes
configure: creating ./config.status
config.status: creating Makefile
config.status: creating scripts/Makefile
config.status: creating data/Makefile
config.status: creating themes/Makefile
config.status: creating scripts/kiba-amarok.py
config.status: creating scripts/kiba-mail.py
config.status: creating scripts/kiba-weather.py
config.status: creating scripts/kiba-signal.py
config.status: creating scripts/kiba-battery.py
config.status: creating scripts/kiba-feeder.py
config.status: creating scripts/quod_dbus_cover.py
config.status: creating scripts/firefox.py
config.status: creating po/Makefile.in
config.status: creating config.h
config.status: executing depfiles commands
config.status: executing intltool commands
config.status: executing default-1 commands
config.status: executing po/stamp-it commands

Kiba library dir :       /usr/local/lib
Kiba data dir:           /usr/local/share

ashu@ashu-laptop:~/kiba-dock/kiba-dbus-plugins$ sudo make install
Making install in scripts
make[1]: Entering directory `/home/ashu/kiba-dock/kiba-dbus-plugins/scripts'
make[2]: Entering directory `/home/ashu/kiba-dock/kiba-dbus-plugins/scripts'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/kiba-dock/dbus_scripts" || mkdir -p -- "/usr/local/share/kiba-dock/dbus_scripts"
 /usr/bin/install -c 'kiba-mail.py' '/usr/local/share/kiba-dock/dbus_scripts/kiba-mail.py'
 /usr/bin/install -c 'kiba-weather.py' '/usr/local/share/kiba-dock/dbus_scripts/kiba-weather.py'
 /usr/bin/install -c 'kiba-signal.py' '/usr/local/share/kiba-dock/dbus_scripts/kiba-signal.py'
 /usr/bin/install -c 'kiba-battery.py' '/usr/local/share/kiba-dock/dbus_scripts/kiba-battery.py'
 /usr/bin/install -c 'kiba-feeder.py' '/usr/local/share/kiba-dock/dbus_scripts/kiba-feeder.py'
make[2]: Leaving directory `/home/ashu/kiba-dock/kiba-dbus-plugins/scripts'
make[1]: Leaving directory `/home/ashu/kiba-dock/kiba-dbus-plugins/scripts'
Making install in data
make[1]: Entering directory `/home/ashu/kiba-dock/kiba-dbus-plugins/data'
sed -e "s|%prefix%|/usr/local|" \
        python_scripts.xml.in.in > python_scripts.xml.in
LC_ALL=C ../intltool-merge -x -u -c ../po/.intltool-merge-cache ../po python_scripts.xml.in python_scripts.xml
Generating and caching the translation database
NOTICE: ../po/it.po is not in UTF-8 but iso-8859-1, converting...
Merging translations into python_scripts.xml.
CREATED python_scripts.xml
make[2]: Entering directory `/home/ashu/kiba-dock/kiba-dbus-plugins/data'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/kiba-dock/config_schemas/plugins" || mkdir -p -- "/usr/local/share/kiba-dock/config_schemas/plugins"
 /usr/bin/install -c -m 644 'python_scripts.xml' '/usr/local/share/kiba-dock/config_schemas/plugins/python_scripts.xml'
make[2]: Leaving directory `/home/ashu/kiba-dock/kiba-dbus-plugins/data'
make[1]: Leaving directory `/home/ashu/kiba-dock/kiba-dbus-plugins/data'
Making install in themes
make[1]: Entering directory `/home/ashu/kiba-dock/kiba-dbus-plugins/themes'
make[2]: Entering directory `/home/ashu/kiba-dock/kiba-dbus-plugins/themes'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/kiba-dock/icons/kiba-battery" || mkdir -p -- "/usr/local/share/kiba-dock/icons/kiba-battery"
 /usr/bin/install -c -m 644 'kiba-battery/none.png' '/usr/local/share/kiba-dock/icons/kiba-battery/none.png'
 /usr/bin/install -c -m 644 'kiba-battery/0.png' '/usr/local/share/kiba-dock/icons/kiba-battery/0.png'
 /usr/bin/install -c -m 644 'kiba-battery/25.png' '/usr/local/share/kiba-dock/icons/kiba-battery/25.png'
 /usr/bin/install -c -m 644 'kiba-battery/50.png' '/usr/local/share/kiba-dock/icons/kiba-battery/50.png'
 /usr/bin/install -c -m 644 'kiba-battery/75.png' '/usr/local/share/kiba-dock/icons/kiba-battery/75.png'
 /usr/bin/install -c -m 644 'kiba-battery/100.png' '/usr/local/share/kiba-dock/icons/kiba-battery/100.png'
test -z "/usr/local/share/kiba-dock/icons/kiba-feeder" || mkdir -p -- "/usr/local/share/kiba-dock/icons/kiba-feeder"
 /usr/bin/install -c -m 644 'kiba-feeder/new.png' '/usr/local/share/kiba-dock/icons/kiba-feeder/new.png'
 /usr/bin/install -c -m 644 'kiba-feeder/old.png' '/usr/local/share/kiba-dock/icons/kiba-feeder/old.png'
test -z "/usr/local/share/kiba-dock/icons/kiba-mail" || mkdir -p -- "/usr/local/share/kiba-dock/icons/kiba-mail"
 /usr/bin/install -c -m 644 'kiba-mail/new.png' '/usr/local/share/kiba-dock/icons/kiba-mail/new.png'
 /usr/bin/install -c -m 644 'kiba-mail/none.png' '/usr/local/share/kiba-dock/icons/kiba-mail/none.png'
test -z "/usr/local/share/kiba-dock/icons/kiba-signal" || mkdir -p -- "/usr/local/share/kiba-dock/icons/kiba-signal"
 /usr/bin/install -c -m 644 'kiba-signal/0.png' '/usr/local/share/kiba-dock/icons/kiba-signal/0.png'
 /usr/bin/install -c -m 644 'kiba-signal/20.png' '/usr/local/share/kiba-dock/icons/kiba-signal/20.png'
 /usr/bin/install -c -m 644 'kiba-signal/40.png' '/usr/local/share/kiba-dock/icons/kiba-signal/40.png'
 /usr/bin/install -c -m 644 'kiba-signal/60.png' '/usr/local/share/kiba-dock/icons/kiba-signal/60.png'
 /usr/bin/install -c -m 644 'kiba-signal/80.png' '/usr/local/share/kiba-dock/icons/kiba-signal/80.png'
 /usr/bin/install -c -m 644 'kiba-signal/100.png' '/usr/local/share/kiba-dock/icons/kiba-signal/100.png'
test -z "/usr/local/share/kiba-dock/icons/kiba-weather" || mkdir -p -- "/usr/local/share/kiba-dock/icons/kiba-weather"
 /usr/bin/install -c -m 644 'kiba-weather/cloud.png' '/usr/local/share/kiba-dock/icons/kiba-weather/cloud.png'
 /usr/bin/install -c -m 644 'kiba-weather/dayfog.png' '/usr/local/share/kiba-dock/icons/kiba-weather/dayfog.png'
 /usr/bin/install -c -m 644 'kiba-weather/daysnow.png' '/usr/local/share/kiba-dock/icons/kiba-weather/daysnow.png'
 /usr/bin/install -c -m 644 'kiba-weather/moon.png' '/usr/local/share/kiba-dock/icons/kiba-weather/moon.png'
 /usr/bin/install -c -m 644 'kiba-weather/nightfog.png' '/usr/local/share/kiba-dock/icons/kiba-weather/nightfog.png'
 /usr/bin/install -c -m 644 'kiba-weather/nightsnow.png' '/usr/local/share/kiba-dock/icons/kiba-weather/nightsnow.png'
 /usr/bin/install -c -m 644 'kiba-weather/snow.png' '/usr/local/share/kiba-dock/icons/kiba-weather/snow.png'
 /usr/bin/install -c -m 644 'kiba-weather/daycloud.png' '/usr/local/share/kiba-dock/icons/kiba-weather/daycloud.png'
 /usr/bin/install -c -m 644 'kiba-weather/dayrain.png' '/usr/local/share/kiba-dock/icons/kiba-weather/dayrain.png'
 /usr/bin/install -c -m 644 'kiba-weather/fog.png' '/usr/local/share/kiba-dock/icons/kiba-weather/fog.png'
 /usr/bin/install -c -m 644 'kiba-weather/nightcloud.png' '/usr/local/share/kiba-dock/icons/kiba-weather/nightcloud.png'
 /usr/bin/install -c -m 644 'kiba-weather/nightrain.png' '/usr/local/share/kiba-dock/icons/kiba-weather/nightrain.png'
 /usr/bin/install -c -m 644 'kiba-weather/raincloud.png' '/usr/local/share/kiba-dock/icons/kiba-weather/raincloud.png'
 /usr/bin/install -c -m 644 'kiba-weather/sun.png' '/usr/local/share/kiba-dock/icons/kiba-weather/sun.png'
make[2]: Leaving directory `/home/ashu/kiba-dock/kiba-dbus-plugins/themes'
make[1]: Leaving directory `/home/ashu/kiba-dock/kiba-dbus-plugins/themes'
Making install in po
make[1]: Entering directory `/home/ashu/kiba-dock/kiba-dbus-plugins/po'
file=`echo de | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file de.po
file=`echo es | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file es.po
file=`echo it | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file it.po
file=`echo ja | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file ja.po
file=`echo pt | sed 's,.*/,,'`.gmo \
          && rm -f $file && /usr/bin/msgfmt -o $file pt.po
/home/ashu/kiba-dock/kiba-dbus-plugins/install-sh -d /usr/local/share/locale
linguas="de es it ja pt "; \
        for lang in $linguas; do \
          dir=/usr/local/share/locale/$lang/LC_MESSAGES; \
          /home/ashu/kiba-dock/kiba-dbus-plugins/install-sh -d $dir; \
          if test -r $lang.gmo; then \
            /usr/bin/install -c -m 644 $lang.gmo $dir/kiba-dbus-plugin.mo; \
            echo "installing $lang.gmo as $dir/kiba-dbus-plugin.mo"; \
          else \
            /usr/bin/install -c -m 644 ./$lang.gmo $dir/kiba-dbus-plugin.mo; \
            echo "installing ./$lang.gmo as" \
                 "$dir/kiba-dbus-plugin.mo"; \
          fi; \
          if test -r $lang.gmo.m; then \
            /usr/bin/install -c -m 644 $lang.gmo.m $dir/kiba-dbus-plugin.mo.m; \
            echo "installing $lang.gmo.m as $dir/kiba-dbus-plugin.mo.m"; \
          else \
            if test -r ./$lang.gmo.m ; then \
              /usr/bin/install -c -m 644 ./$lang.gmo.m \
                $dir/kiba-dbus-plugin.mo.m; \
              echo "installing ./$lang.gmo.m as" \
                   "$dir/kiba-dbus-plugin.mo.m"; \
            else \
              true; \
            fi; \
          fi; \
        done
installing de.gmo as /usr/local/share/locale/de/LC_MESSAGES/kiba-dbus-plugin.mo
installing es.gmo as /usr/local/share/locale/es/LC_MESSAGES/kiba-dbus-plugin.mo
installing it.gmo as /usr/local/share/locale/it/LC_MESSAGES/kiba-dbus-plugin.mo
installing ja.gmo as /usr/local/share/locale/ja/LC_MESSAGES/kiba-dbus-plugin.mo
installing pt.gmo as /usr/local/share/locale/pt/LC_MESSAGES/kiba-dbus-plugin.mo
make[1]: Leaving directory `/home/ashu/kiba-dock/kiba-dbus-plugins/po'
make[1]: Entering directory `/home/ashu/kiba-dock/kiba-dbus-plugins'
make[2]: Entering directory `/home/ashu/kiba-dock/kiba-dbus-plugins'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/ashu/kiba-dock/kiba-dbus-plugins'
make[1]: Leaving directory `/home/ashu/kiba-dock/kiba-dbus-plugins'
ashu@ashu-laptop:~/kiba-dock/kiba-dbus-plugins$ cd ..
ashu@ashu-laptop:~/kiba-dock$ 
```

---

### Post by mattgaunt on 2008-02-04
ok by running it with kiba-dock & you essentially saying run kiba-dock and give me use of the terminal again, i think with that error, kiba-dock still runs doesnt it??

Anyway my point was, with kiba-dock & the error msg is still happening but its hidden from you is all

Unfortunately i had that problem and i think its got something to do with kiba-dock not having the right permissions to create the directory or something, but I am only guessin

Gaunt

---

### Post by intense.ego on 2008-02-04
Except for the cool physics that I heard of (but found out does not work atm), kiba-dock seems to be working fine. Are there any cool special effects i can add, like explosions and the twists and jumps I have seen on videos?

---

### Post by rabbot on 2008-02-04
> **mattgaunt said:**
> rabbot did u get any messages come up during the process of the how-to??

Gaunt

It's kinda hard to keep track =/

I'm gonna try uninstalling it and then reinstalling it again. I'm using 64-bit, by the way,

---

### Post by LouisChappell on 2008-02-04
Is there a way of scrolling through the icons in such a way as a mac does? i've filled my dock and pretty much solely use it for most of my needs at the moment it's on top and fills the top but when i move it to the left or right it just misses a few out, any way of sorting this out? i've looked through kiba settings to no avail.

---

### Post by braks on 2008-02-05
This is how I got my kiba-dock working with a minor change from matt's guide.  I have been getting the Segmentation fault (core dumped) error before.
Running ubuntu 7.10 32bit.  Btw great guide and thanks a lot.

In terminal, stay in user mode '$' (for those who created a password for root)

Include the '--prefix=/usr --exec-prefix=/usr' after each './autogen.sh'

Type 'make' before typing 'sudo make install'


So for instance when you get to the codes for 32 bit ubuntu users, instead of doing this...
> ```
cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
sudo make install
cd ..
```

do this...
```
cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
make
sudo make install
cd ..

```

Repeat this the same way for kiba-dock/, kiba-plugins/ and kiba-dbus-plugins/ and thats it!  I will play around with kiba-dock and see if any other problems arise.  Then ill try it on 64 bit and let you know if it works.:)

---

### Post by intense.ego on 2008-02-05
So, do I have to uninstall and then reinstall?

---

### Post by mattgaunt on 2008-02-05
Alot of the problems you guys are having with kiba-dock I have put done to the programming of kiba-dock rather than the install. I could be wrong but that is my impression since kiba-dock isnt particularly stable and never seems to have big updates in a release

I am jus giving my impression though, i could be very very wrong!!

Gaunt

---

### Post by santiagoward2000 on 2008-02-05
Hi there!
I was trying to get the **Trash** plugin working on Xubuntu, so I asked on Kiba's forum and danielb told me to: > the trash plugin uses gnome libs, you can link the gnome trash dir to the xfce trash dir, that may work.
also you should compile with --enable-xfce, then thunar should be launched when clicking the trash

How do I **compile with --enable-xfce**?
Thank you!

---

### Post by g0vP on 2008-02-05
how can i stop AWN from opening when i boot/login?

---

### Post by LouisChappell on 2008-02-05
@ g0vP is it unchecked on system>preferences>sessions?

---

### Post by santiagoward2000 on 2008-02-05
> **santiagoward2000 said:**
> Hi there!
I was trying to get the **Trash** plugin working on Xubuntu, so I asked on Kiba's forum and danielb told me to: 
How do I **compile with --enable-xfce**?
Thank you!

Never mind, I figured it out! :D All I had to do was place **--enable-xfce** right after the ```
./autogen.sh
```
Now my **Trash** plugin is working!!! \\:D/

---

### Post by ronb94 on 2008-02-05
Hello
I am using ubuntu about 2 monts but i am still new
I reinstalled ubuntu and i wanted to install kiba as usual from this Howto
[http://ubuntuforums.org/showthread.php?t=554127](http://ubuntuforums.org/showthread.php?t=554127)
I did exactly like in the 64 bit section(I installed many times kiba-dock before from this Howto and i had no problems)but when i try to run it I am getting this messege:
Segmentation fault (core dumped)
I reinstalled it many times but still no changes.I even tried this script
[http://ubuntuforums.org/showthread.p...pt#post4239236](http://ubuntuforums.org/showthread.p...pt#post4239236)
but i still got the same.
I dont know why i am getting this because i did exactly like i did always to install kiba.
Thanks

---

### Post by Gourgi on 2008-02-05
> **ronb94 said:**
> Hello
I did exactly like in the 64 bit section(I installed many times kiba-dock before from this Howto and i had no problems)but when i try to run it I am getting this messege:
Segmentation fault (core dumped)


i think that for the "segment fault"  error you have to re-install, that is what everyone proposes :KS
i'll try to install it now
 let's see ...


PS , amd64 here too :popcorn:

---

### Post by Gourgi on 2008-02-05
you are right , i tried several times , everything seems to install fine but kiba-dock is not running .. :(
kiba-settings though run! lol

too bad this is a good dock :(

Could someone who has a recently working install of kiba-dock , do the following : 
uninstall everything and reinstall like this :
follow the guide at first post but _replace every instance_ of [COLOR="Blue"]make install[/COLOR] with[COLOR="Blue"] checkinstall [/COLOR] .
Using checkinstall, 4 .deb files will be created (1 for every installed package for kiba).
You can then attach the .deb files somewhere we can download them and use them to see if they work for us 

off course you have to install checkinstall first!
> sudo apt-get install checkinstall

do we have a volunteer for this ?

---

### Post by braks on 2008-02-05
Nice dock for sure but it keeps crashing when the parabola effect/zoom/eyes whatever you wanna call it is applied.  I tried awn which was very stable but lacks the ease of configuration and creating launchers compared to kiba.  I am installing cairo as of now and hoping this will be the one i stick with.

If you have not seen this, here's another guide that got kiba working but the command 'kiba-dock' to run it didn't work for me.  Had to go through the menus.  [_[COLOR="Orange"][U][COLOR="Orange"]http://adznet.info/kiba/index.php/Installation[/COLOR]_[/COLOR][/U]]("http://adznet.info/kiba/index.php/Installation")

Good luck with the efforts!

---

### Post by Gourgi on 2008-02-06
> **braks said:**
> Nice dock for sure but it keeps crashing when the parabola effect/zoom/eyes whatever you wanna call it is applied.  I tried awn which was very stable but lacks the ease of configuration and creating launchers compared to kiba.  I am installing cairo as of now and hoping this will be the one i stick with.

If you have not seen this, here's another guide that got kiba working but the command 'kiba-dock' to run it didn't work for me.  Had to go through the menus.  [_[COLOR="Orange"][U][COLOR="Orange"]http://adznet.info/kiba/index.php/Installation[/COLOR]_[/COLOR][/U]]("http://adznet.info/kiba/index.php/Installation")

Good luck with the efforts!

thanks for the reply , i tried that also but no success :(

---

### Post by g0vP on 2008-02-06
@ LouisChappell
i unticked it, didnt work. tried removing it from the session startup list altogether, but still no luck..

---

### Post by Siyfion on 2008-02-06
I have the same problem as you guys now, "Segmentation fault (core dumped)" and im running an x64 based system.

---

### Post by dark_harmonics on 2008-02-07
I get the segmentation error on 2 64 bit systems. I followed the instructions and I actually have built this software from scratch without a guide before. Everything on the install works but the program just crashes. This really sucks because this is my favourite dock!

---

### Post by mattgaunt on 2008-02-07
It might be a problem with the latest SVN code that the developer is currently fixing, because seems like all of you are having a huge problem and not that many people suffered this problem before

Gaunt

---

### Post by Spydr4590 on 2008-02-07
I followed the requirements from the wiki page on kiba-dock for all build tools needed and even added the ones from here. I installed alot of dev libraries. First it couldn't create a config file. Now all I get are Segmentation fault (core dumped) on 64bit. On various reinstalls the only thing I've been able to get working for kiba dock is the dock will show up but no icons. Frustrating /sigh.

I've tried maybe three weeks ago and had no issues with kiba-dock on 32bit.

Maybe someone can make a working deb for 64bit.

---

### Post by braks on 2008-02-08
So i installed a fresh copy of gusty 64 and tried kiba-dock... no go segmentation fault.  I think im done messing with kiba.  It works on 32 bit with crashes and no go on 64 bit.  Cairo is a thing of beauty :)

---

### Post by dark_harmonics on 2008-02-08
Yea i would agree that after reading here, that kiba-dock code seems to be flawed for the 64 bit platform. Very sad. Oh well, guess its time to check out avant-windows-navigator again.

---

### Post by s14db on 2008-02-10
> **duncan.hawthorne said:**
> 
@greg142
try symlinking /usr/local/lib/kiba-dock to /usr/lib/kiba-dock (looks like the plugins are being installed in the wrong folder)
ie run:
sudo ln -s /usr/lib/kiba-dock /usr/local/lib/kiba-dock

I still get:

** (kiba-dock:29800): WARNING **: Error (main.c @ line 243):
        Failed to locate Plugins at '/usr/local/lib/kiba-dock'
Please install the Plugins at '/usr/local/lib/kiba-dock' or use the '--plugin-path' command line parameter.

---

### Post by dinkdrmr on 2008-02-18
ok .. i didn't get any errors on install, but for some reason when i go into applications>accessories>kiba dock it doesn't open. 

I can get into the settings, but the dock won't start itself

---

### Post by ronb94 on 2008-02-18
Kiba-Dock is not working at last on the 64bit. I am waiting too for a solution.

---

### Post by Jermeezy on 2008-02-20
jermzlove@Jermzlove:~$ ** (kiba-dock:1236): WARNING **: Error (dbus.c @ line 989):
bash: syntax error near unexpected token `kiba-dock:1236'
jermzlove@Jermzlove:~$         Failed to make connection to session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
bash: Failed: command not found
jermzlove@Jermzlove:~$         For a core dump, run kiba-dock with --g-fatal-warnings.
bash: For: command not found
jermzlove@Jermzlove:~$ 
jermzlove@Jermzlove:~$ ** (kiba-dock:1236): WARNING **: Error (plugin.c @ line 242):
bash: syntax error near unexpected token `kiba-dock:1236'
jermzlove@Jermzlove:~$         '/usr/local/lib/kiba-dock/libdbus.so' is not loadable
Segmentation fault (core dumped)
jermzlove@Jermzlove:~$ 
jermzlove@Jermzlove:~$         For a core dump, run kiba-dock with --g-fatal-warnings.
bash: For: command not found
jermzlove@Jermzlove:~$ kiba-dock --g-fatal-warnings

Gdk-CRITICAL **: gdk_screen_get_monitor_geometry: assertion `monitor_num < GDK_SCREEN_X11 (screen)->num_monitors' failed
aborting...
Aborted (core dumped)
jermzlove@Jermzlove:~$ --g-fatal-warnings

---

### Post by lepine002 on 2008-02-20
how long do you think it will be before you can install kiba dock on the 64 bit?

---

### Post by mattgaunt on 2008-02-21
Ud hav to ask on the kiba-dock forums, see if anyone has a fix, or if anyone knows what the problem is and if the developer / developers are aware of it or not

Gaunt

---

### Post by natedogg624 on 2008-02-22
i had it working when i typed kiba-dock in the terminal it popped up like it should!

but then i closed terminal and the dock went away as well...:(  then the next page i read i should have done kiba-dock &

anyway i can get it back without having to install it again?

---

### Post by SomeGuyDude on 2008-02-22
> **natedogg624 said:**
> i had it working when i typed kiba-dock in the terminal it popped up like it should!

but then i closed terminal and the dock went away as well...:(  then the next page i read i should have done kiba-dock &

anyway i can get it back without having to install it again?

That'll happen with any app. Open something in the terminal, then close the terminal and the app will close as well. Try it with Firefox or GIMP or something. Hit Alt+F2 and type it again.

---

### Post by natedogg624 on 2008-02-22
yup did that its listed in the applications but it wont come on...i can get into settings and such but not the actual dock itself.

also it came on when i started my computer, but there was no background to it, just floating icons on an invisible platform.  and as soon as i changed a setting it disappeared and i haven't been able to get it back. 

what do you think about this?

---

### Post by kennyn1980 on 2008-02-22
Hope someone can advise here!
Please be aware I am a Linux n00b :(

I followed all the instructions at the beginning of this post. I THINK everything installed as it should.

Kiba-dock and kiba settings appear in Applications -> Accessories but when I try to run kiba-dock I get this which means nothing to me!!!

kenny@KennysPC:~$ kiba-dock
*** glibc detected *** kiba-dock: free(): invalid pointer: 0x00002abba5e039e0 ***
======= Backtrace: =========
/lib/libc.so.6[0x2abba5b1eb0a]
/lib/libc.so.6(cfree+0x8c)[0x2abba5b226fc]
kiba-dock[0x42974c]
kiba-dock(kiba_prefs_add_callback+0xb0)[0x4283e0]
kiba-dock(kiba_prefs_callbacks_add+0xef)[0x42950f]
kiba-dock(main+0x344)[0x412514]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2abba5acab44]
kiba-dock[0x412139]
======= Memory map: ========
00400000-0044d000 r-xp 00000000 08:01 5540740                            /usr/bin/kiba-dock
0064d000-0064f000 rw-p 0004d000 08:01 5540740                            /usr/bin/kiba-dock
0064f000-00757000 rw-p 0064f000 00:00 0                                  [heap]
2abba180a000-2abba1827000 r-xp 00000000 08:01 20594700                   /lib/ld-2.6.1.so
2abba1827000-2abba182a000 rw-p 2abba1827000 00:00 0 
2abba182a000-2abba1831000 r--s 00000000 08:01 5554699                    /usr/lib/gconv/gconv-modules.cache
2abba1a26000-2abba1a28000 rw-p 0001c000 08:01 20594700                   /lib/ld-2.6.1.so
2abba1a28000-2abba1df9000 r-xp 00000000 08:01 5539517                    /usr/lib/libgtk-x11-2.0.so.0.1200.0
2abba1df9000-2abba1ff8000 ---p 003d1000 08:01 5539517                    /usr/lib/libgtk-x11-2.0.so.0.1200.0
2abba1ff8000-2abba2004000 rw-p 003d0000 08:01 5539517                    /usr/lib/libgtk-x11-2.0.so.0.1200.0
2abba2004000-2abba2006000 rw-p 2abba2004000 00:00 0 
2abba2006000-2abba209f000 r-xp 00000000 08:01 5539362                    /usr/lib/libgdk-x11-2.0.so.0.1200.0
2abba209f000-2abba229f000 ---p 00099000 08:01 5539362                    /usr/lib/libgdk-x11-2.0.so.0.1200.0
2abba229f000-2abba22a4000 rw-p 00099000 08:01 5539362                    /usr/lib/libgdk-x11-2.0.so.0.1200.0
2abba22a4000-2abba22c2000 r-xp 00000000 08:01 5539181                    /usr/lib/libatk-1.0.so.0.2009.1
2abba22c2000-2abba24c2000 ---p 0001e000 08:01 5539181                    /usr/lib/libatk-1.0.so.0.2009.1
2abba24c2000-2abba24c5000 rw-p 0001e000 08:01 5539181                    /usr/lib/libatk-1.0.so.0.2009.1
2abba24c5000-2abba24de000 r-xp 00000000 08:01 5539364                    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
2abba24de000-2abba26de000 ---p 00019000 08:01 5539364                    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
2abba26de000-2abba26df000 rw-p 00019000 08:01 5539364                    /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
2abba26df000-2abba26e0000 rw-p 2abba26df000 00:00 0 
2abba26e0000-2abba2760000 r-xp 00000000 08:01 20595277                   /lib/libm-2.6.1.so
2abba2760000-2abba295f000 ---p 00080000 08:01 20595277                   /lib/libm-2.6.1.so
2abba295f000-2abba2961000 rw-p 0007f000 08:01 20595277                   /lib/libm-2.6.1.so
2abba2961000-2abba296b000 r-xp 00000000 08:01 5537910                    /usr/lib/libpangocairo-1.0.so.0.1800.3
2abba296b000-2abba2b6a000 ---p 0000a000 08:01 5537910                    /usr/lib/libpangocairo-1.0.so.0.1800.3
2abba2b6a000-2abba2b6b000 rw-p 00009000 08:01 5537910                    /usr/lib/libpangocairo-1.0.so.0.1800.3
2abba2b6b000-2abba2b96000 r-xp 00000000 08:01 5539316                    /usr/lib/libfontconfig.so.1.2.0
2abba2b96000-2abba2d95000 ---p 0002b000 08:01 5539316                    /usr/lib/libfontconfig.so.1.2.0
2abba2d95000-2abba2da0000 rw-p 0002a000 08:01 5539316                    /usr/lib/libfontconfig.so.1.2.0
2abba2da0000-2abba2da1000 rw-p 2abba2da0000 00:00 0 
2abba2da1000-2abba2db2000 r-xp 00000000 08:01 5539123                    /usr/lib/libXext.so.6.4.0
2abba2db2000-2abba2fb1000 ---p 00011000 08:01 5539123                    /usr/lib/libXext.so.6.4.0
2abba2fb1000-2abba2fb2000 rw-p 00010000 08:01 5539123                    /usr/lib/libXext.so.6.4.0
2abba2fb2000-2abba2fbb000 r-xp 00000000 08:01 5539145                    /usr/lib/libXrender.so.1.3.0
2abba2fbb000-2abba31ba000 ---p 00009000 08:01 5539145                    /usr/lib/libXrender.so.1.3.0
2abba31ba000-2abba31bb000 rw-p 00008000 08:01 5539145                    /usr/lib/libXrender.so.1.3.0
2abba31bb000-2abba31bd000 r-xAborted (core dumped)


Can anyone help with this?! It would be much appreciated!!

---

### Post by hananias on 2008-02-23
I followed all instruction in the beginning of this forum, and it all install ok...except when i try to run in terminal I get this message:

Segmentation fault (core dumped)

What does this mean?  Well, I have an idea something went wrong in the installation, but how do i fix it???

---

### Post by mattgaunt on 2008-02-24
hananias are you running 64 bit version of ubuntu??

Cos if u are i think (judgin by the number of responses) kiba-dock isnt working properly for the 64-bit version at the moment

Gaunt

---

### Post by ronb94 on 2008-02-24
> **mattgaunt said:**
> hananias are you running 64 bit version of ubuntu??

Cos if u are i think (judgin by the number of responses) kiba-dock isnt working properly for the 64-bit version at the moment

Gaunt

I think that kiba isn't running at all. On the 64bit there is problem with Segmentation fault (core dumped) and with the 32bit( I tried it yesterday) its not working too
> *** glibc detected *** kiba-dock: free(): invalid pointer: 0x00002abba5e039e0 ***
======= Backtrace: =========
/lib/libc.so.6[0x2abba5b1eb0a]
/lib/libc.so.6(cfree+0x8c)[0x2abba5b226fc]
kiba-dock[0x42974c]
kiba-dock(kiba_prefs_add_callback+0xb0)[0x4283e0]
kiba-dock(kiba_prefs_callbacks_add+0xef)[0x42950f]
kiba-dock(main+0x344)[0x412514]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2abba5acab44]
kiba-dock[0x412139]
======= Memory map: ========
00400000-0044d000 r-xp 00000000 08:01 5540740 /usr/bin/kiba-dock
0064d000-0064f000 rw-p 0004d000 08:01 5540740 /usr/bin/kiba-dock
0064f000-00757000 rw-p 0064f000 00:00 0 [heap]
2abba180a000-2abba1827000 r-xp 00000000 08:01 20594700 /lib/ld-2.6.1.so
2abba1827000-2abba182a000 rw-p 2abba1827000 00:00 0
2abba182a000-2abba1831000 r--s 00000000 08:01 5554699 /usr/lib/gconv/gconv-modules.cache
2abba1a26000-2abba1a28000 rw-p 0001c000 08:01 20594700 /lib/ld-2.6.1.so
2abba1a28000-2abba1df9000 r-xp 00000000 08:01 5539517 /usr/lib/libgtk-x11-2.0.so.0.1200.0
2abba1df9000-2abba1ff8000 ---p 003d1000 08:01 5539517 /usr/lib/libgtk-x11-2.0.so.0.1200.0
2abba1ff8000-2abba2004000 rw-p 003d0000 08:01 5539517 /usr/lib/libgtk-x11-2.0.so.0.1200.0
2abba2004000-2abba2006000 rw-p 2abba2004000 00:00 0
2abba2006000-2abba209f000 r-xp 00000000 08:01 5539362 /usr/lib/libgdk-x11-2.0.so.0.1200.0
2abba209f000-2abba229f000 ---p 00099000 08:01 5539362 /usr/lib/libgdk-x11-2.0.so.0.1200.0
2abba229f000-2abba22a4000 rw-p 00099000 08:01 5539362 /usr/lib/libgdk-x11-2.0.so.0.1200.0
2abba22a4000-2abba22c2000 r-xp 00000000 08:01 5539181 /usr/lib/libatk-1.0.so.0.2009.1
2abba22c2000-2abba24c2000 ---p 0001e000 08:01 5539181 /usr/lib/libatk-1.0.so.0.2009.1
2abba24c2000-2abba24c5000 rw-p 0001e000 08:01 5539181 /usr/lib/libatk-1.0.so.0.2009.1
2abba24c5000-2abba24de000 r-xp 00000000 08:01 5539364 /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
2abba24de000-2abba26de000 ---p 00019000 08:01 5539364 /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
2abba26de000-2abba26df000 rw-p 00019000 08:01 5539364 /usr/lib/libgdk_pixbuf-2.0.so.0.1200.0
2abba26df000-2abba26e0000 rw-p 2abba26df000 00:00 0
2abba26e0000-2abba2760000 r-xp 00000000 08:01 20595277 /lib/libm-2.6.1.so
2abba2760000-2abba295f000 ---p 00080000 08:01 20595277 /lib/libm-2.6.1.so
2abba295f000-2abba2961000 rw-p 0007f000 08:01 20595277 /lib/libm-2.6.1.so
2abba2961000-2abba296b000 r-xp 00000000 08:01 5537910 /usr/lib/libpangocairo-1.0.so.0.1800.3
2abba296b000-2abba2b6a000 ---p 0000a000 08:01 5537910 /usr/lib/libpangocairo-1.0.so.0.1800.3
2abba2b6a000-2abba2b6b000 rw-p 00009000 08:01 5537910 /usr/lib/libpangocairo-1.0.so.0.1800.3
2abba2b6b000-2abba2b96000 r-xp 00000000 08:01 5539316 /usr/lib/libfontconfig.so.1.2.0
2abba2b96000-2abba2d95000 ---p 0002b000 08:01 5539316 /usr/lib/libfontconfig.so.1.2.0
2abba2d95000-2abba2da0000 rw-p 0002a000 08:01 5539316 /usr/lib/libfontconfig.so.1.2.0
2abba2da0000-2abba2da1000 rw-p 2abba2da0000 00:00 0
2abba2da1000-2abba2db2000 r-xp 00000000 08:01 5539123 /usr/lib/libXext.so.6.4.0
2abba2db2000-2abba2fb1000 ---p 00011000 08:01 5539123 /usr/lib/libXext.so.6.4.0
2abba2fb1000-2abba2fb2000 rw-p 00010000 08:01 5539123 /usr/lib/libXext.so.6.4.0
2abba2fb2000-2abba2fbb000 r-xp 00000000 08:01 5539145 /usr/lib/libXrender.so.1.3.0
2abba2fbb000-2abba31ba000 ---p 00009000 08:01 5539145 /usr/lib/libXrender.so.1.3.0
2abba31ba000-2abba31bb000 rw-p 00008000 08:01 5539145 /usr/lib/libXrender.so.1.3.0
2abba31bb000-2abba31bd000 r-xAborted (core dumped)

---

### Post by mattgaunt on 2008-02-24
segmentation fault normally has something to do with a stray pointer or memory leak somewhere in the program. But I have no idea on how to debug the problem  if it is a problem with the kiba-dock, otherwise it could be a problem with a library perhaps but alot less likely

Gaunt

---

### Post by mario1o1 on 2008-02-26
i am new to linux and i figured out how to install kiba-dock and everything but how do you make the icons bounce off each other i cant find it in the settings? thanks

---

### Post by mattgaunt on 2008-02-27
merio1o1 last time i knew, the akamaru (physics engine) wasn't working, which is the bit i think u r tlkin about.

Gaunt

---

### Post by Umut Ya&#351;ar on 2008-02-27
I followed the instruction and installed kiba dock but when I typed it in terminal, it seems working well but terminal says;

```
   ** (kiba-dock:5799): WARNING **: Error (sysinfo.c @ line 441):
        KibaSysinfo: failed to load theme

        For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:5799): WARNING **: Error (sysinfo.c @ line 441):
        KibaSysinfo: failed to load theme

        For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:5799): WARNING **: Error (sysinfo.c @ line 441):
        KibaSysinfo: failed to load theme

        For a core dump, run kiba-dock with --g-fatal-warnings.

```

and then when I try to use icons on dock panel, the panel goes away. What can I do?..

---

### Post by talsemgeest on 2008-03-01
So is there any way to get the physics engine running?

---

### Post by talsemgeest on 2008-03-01
Oh, I forgot to thank you for such an awesome how-to!

So thanks!

---

### Post by HoLLyw00dGT on 2008-03-03
I copied everything line by line and i typed kiba-dock in terminal and "Command not found" >_<

---

### Post by talsemgeest on 2008-03-03
Are you sure you followed the instructions exactly? Like where it said to do it one line at a time?

---

### Post by wanchai on 2008-03-06
I'm trying to install Kiba on Gutsy following the steps outlined in the first post of this thread. Ran into some problems in the "plugin" step, it complained that there is no kiba-dock package. Then I repeated everything with the prefix parameters in all autogen steps. Finally it compiled.

Then I downlaoded 
[http://ubunteros.free.fr/kiba.schemas](http://ubunteros.free.fr/kiba.schemas)
and ran
gconftool-2 --install-schema-file=kiba.schemas

Now I can start kiba-dock, but I can't do anything with it. When I try to run kiba-settings it complains "No valid .schema file(s) found". Can anyone help? What are these .schema files, where are they supposed to be and where can I get them from if they're not there?

---

### Post by locosmurf on 2008-03-06
great how-to man thanx!!!

but I have one small problem... I've searched all over the forums and I googled the problem and I've come up with nothing so here goes.....

I installed everything from the how-to and I've managed to get kiba up and running no sweat but for some reason akamaru doesn't appear to exist. when I compiled the akamaru part it entered a the directories but said that nothing needed to be done so I'm not even sure if its installed or not. if it isn't what do I do? and if it is how do I get it to run?

I'm using Ubuntu 7.10 and I have compiz-fusion running just fine.

thanx in advance for the help!!!

---

### Post by talsemgeest on 2008-03-06
Probably something to do with the non-existing physics engine.

It got removed because of "bad implementation", so we just have to be patient and wait for it to be re-implemented

---

### Post by locosmurf on 2008-03-06
thanx talsemgeest its just that everyone appears to have it working but nobody really says how. I think i might have found a fix so I'm going to try that and see what happens. I'll post it if it does!!!

edit:
so apparently the package I thought I was missing (intltools) I actually had so that wasn't the problem. I'm officially stumped and hope that they get the physics engine working right soon because thats the whole reason I installed kiba (although I'm going to keep it regardless because I like it so much even without akamaru lol)

---

### Post by duncan.hawthorne on 2008-03-08
akamaru (ie physics) has been removed in the current svn build, (maybe it will be put back in soon)
however, this isnt really a problem, svn gives you access to all the old builds. you could just change revision to one of the old builds at random, or someone could  post the build they have that works

something like
 svn update -r 500 * 
would download revision 500 of all files, then you can find on with akamaru.
hope this helps

---

### Post by wanchai on 2008-03-08
The problem with the .schema file I asked about earlier is gone. I uninstalled everything then reinstalled with
```
./autogen.sh --prefix=/usr --exec-prefix=/usr
make
sudo make install
```
for all four components. Then it suddenly worked. If I use the 'prefix' only for akamaru as described in the first post of this thread, then autogen will fail for the plugin with a complaint that kiba-dock doesn't exist.

One more thing: the bit about this gconf is not needed. I found this somewhere on the web, but danielb said in his forum that kiba-dock doesn't use gconf.

That's my two cents worth of feedback. Now, if there were a way to save separators and specify the order of launchers, then I'd might actually keep this thing, but tomorrow I'm going to try out cairo-dock...

---

### Post by richard2121 on 2008-03-08
Will this work in KDE4 with compiz?

---

### Post by talsemgeest on 2008-03-08
Just checked, the last release with akamaru and the physics engine is 602. From 603 onwards there are no physics, so I'm using 602 for now

---

### Post by talsemgeest on 2008-03-08
Ok, so I've got akamaru working, but there is something seriously wrong with my icons. Whenever the physics is on, all of my icons startup as white blocks. When I restart the physics, everything is fine, until a new icon pops up, which is instantly a white block as well. Oh and when physics is on, the icons are behind the dock. 

Any ideas?
Thanks in advance

---

### Post by Xrigid17X on 2008-03-17
WOW thanks bro this installed without a problem.:guitar::guitar:

---

### Post by talsemgeest on 2008-03-17
> **Xrigid17X said:**
> WOW thanks bro this installed without a problem.:guitar::guitar:
Have you got physics?

---

### Post by peachstone on 2008-03-18
can someone help with my errors? I am pretty new to this as well

checking pkg-config is at least version 0.9.0... yes
checking for KIBA_DOCK... configure: error: Package requirements (kiba-dock = 9999) were not met:

No package 'kiba-dock' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables KIBA_DOCK_CFLAGS
and KIBA_DOCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

mike@mike-desktop:~/kiba/kiba-plugins$ make
make: *** No targets specified and no makefile found.  Stop.

Thanks

---

### Post by peachstone on 2008-03-18
can someone help with my errors? I am pretty new to this as well

checking pkg-config is at least version 0.9.0... yes
checking for KIBA_DOCK... configure: error: Package requirements (kiba-dock = 9999) were not met:

No package 'kiba-dock' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables KIBA_DOCK_CFLAGS
and KIBA_DOCK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

mike@mike-desktop:~/kiba/kiba-plugins$ make
make: *** No targets specified and no makefile found. Stop.

---

### Post by talsemgeest on 2008-03-18
Are you sure you have followed all the instructions down to the line? Also where did you get this error?

---

### Post by amrith on 2008-03-18
That was a cool HOW-TO !!!! 
Thank you..

Can you tell me which setting in Kiba-dock would make the icons on the dock show elasticity ? 

Thanks.

---

### Post by talsemgeest on 2008-03-18
> **amrith said:**
> That was a cool HOW-TO !!!! 
Thank you..

Can you tell me which setting in Kiba-dock would make the icons on the dock show elasticity ? 

Thanks.
Read the last couple of pages of this thread. 

The physics engine has been temporarily removed. You just have to be patient and wait for it to be put back in, or you can install an older version that still had the physics in it.

---

### Post by terrax on 2008-03-18
If you want the deb's instead:
[http://ubuntuforums.org/showthread.php?t=728231]("http://ubuntuforums.org/showthread.php?t=728231")

Newly fresh builded.

---

### Post by missiledave on 2008-03-31
wonderful guide, thank you, 32 bit install worked perfectly!  keep these guides coming!

---

### Post by Victormd on 2008-03-31
VERY NICE!!!!  I've had AWN setup for quite a while now but, as most ubuntu users, we're always looking for something new, or at least challenging... you kind'a took the challenge part away because it worked so well... but, Oh well, we can't have it all! :)

---

### Post by mattgaunt on 2008-04-02
Hey missiledave and victormd or anyone who reads this and tried the how-to can you tell me if the physics engines akamaru worked??


I believe that kiba-dock developers have been re-doing it and for quite a while it wasnt working, is this still the case??

But glad you guys liked it

Gaunt

---

### Post by Datanizze on 2008-04-06
> **mattgaunt said:**
> Hey missiledave and victormd or anyone who reads this and tried the how-to can you tell me if the physics engines akamaru worked??
Gaunt

i'm totally new to linux and i did not get the physics engine working, tried reinstalling it twice but with no luck. :(

---

### Post by talsemgeest on 2008-04-06
Physics engine is gone. Last version that still had it was 602.

---

### Post by mattgaunt on 2008-04-08
fair enough, was just wondering if the developer had fixed / re-written the code for it

Gaunt

---

### Post by talsemgeest on 2008-04-08
Yeah, I'm still waiting...

---

### Post by tettayes on 2008-04-09
Hi, i followed ur how-to and got this when i did kiba-dock

```

tetta@tettasama:~$ kiba-dock

** (kiba-dock:12491): WARNING **: Error (plugin-loader.c @ line 632):
	Failed to open Plugin Directory '/usr/local/lib/kiba-dock/global_plugins': Error opening directory '/usr/local/lib/kiba-dock/global_plugins': No such file or directory

	For a core dump, run kiba-dock with --g-fatal-warnings.

```

any suggestions would be appreciated!

---

### Post by SaturnBurst on 2008-04-09
Hi,

I just followed the 32-bit version and got the same error as tettayes.

Help would be very much appreciated!

Cheers,
SaturnBurst

---

### Post by +peter on 2008-04-09
wow, I just attempted to install for the first time and had the same error as both SaturnBurst and tettayes

---

### Post by CJay554 on 2008-04-09
bump

---

### Post by eigenstil on 2008-04-10
i get exactly the same error when starting. anyone knows a solution?

---

### Post by Piteco on 2008-04-10
I can't install the kiba-plugins...
this is the error :

> lucas@lucas-desktop:~$ kiba-dock
The program 'kiba-dock' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 1394 error_code 8 request_code 157 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I'm new with Ubuntu, hope you guys can help me (:

---

### Post by mattgaunt on 2008-04-10
Sorry guys, all I can suggest is try asking in the kiba-dock forum on [www.kiba-dock.org](www.kiba-dock.org) I cant fix i problem that i never had.

If you guys do find a fix please send me a message ill write it up on the how-to once others have confirmed it works.

Gaunt

---

### Post by Burmuda on 2008-04-10
Just create the directory:
# sudo mkdir /usr/local/lib/kiba-dock/global_plugins

---

### Post by Piteco on 2008-04-10
> **Burmuda said:**
> Just create the directory:
# sudo mkdir /usr/local/lib/kiba-dock/global_plugins

and install what folders inside?

---

### Post by yoshimitsuspeed on 2008-04-10
If it helps I spent hours trying to get this to work on my 64 bit sys with no sucess. There is some trouble with the plugins. I found a workaround but didn't get it to work. 
I found a how to for Cairo dock and it took a matter of minutes and I love it. 
I would love to try kiba-dock at somepoint but if you are looking for something about as good and much easier check this out. 
[http://ph.ubuntuforums.com/showthread.php?t=613087](http://ph.ubuntuforums.com/showthread.php?t=613087)
I don't know if it's been mentioned here, I didn't get all the way through the thread. 
Maybe you could add a mention in the begning of the thread.

---

### Post by Burmuda on 2008-04-11
> **Piteco said:**
> and install what folders inside?
Nothing - just creating it worked fine for me.
I had this error:


```
[** (kiba-dock:12491): WARNING **: Error (plugin-loader.c @ line 632):
	Failed to open Plugin Directory '/usr/local/lib/kiba-dock/global_plugins': Error opening directory '/usr/local/lib/kiba-dock/global_plugins': No such file or directory

```

---

### Post by tettayes on 2008-04-11
Oh my, thanks Burmuda, it worked!

---

### Post by CJay554 on 2008-04-13
Wow, you gta be kidding me, thats all? i tried that but didn't work at first, then i copied the "global_plugins" to make sure its correctly spelled, then again nothing, finally just did the whole directory.

```
sudo mkdir /usr/local/lib/kiba-dock/global_plugins
```

works like a charm =]
thanks bunch! Cairo-dock was getting a bit bland...

---

### Post by freaky behavior on 2008-04-20
i cant get it to work. when i follow the steps i doesnt give me any errors at all but when i type in kiba-dock at the end it says no such file or directory

and i tried the global plugins n this is what it gave me

bach@bach-desktop:~/kiba-dock/akamaru$ sudo mkdir /usr/local/lib/kiba-dock/global_plugins
mkdir: cannot create directory `/usr/local/lib/kiba-dock/global_plugins': No such file or directory

---

### Post by dover19 on 2008-04-21
I couldn never to get this tow ork properly and when I tried uninstalling it I couldn't even do that.

I can't even find the folder for it.

---

### Post by mattgaunt on 2008-04-23
The folder should be kiba-dock in your home folder if you followed the how-to

If its not there then thats a bit weird :-S

---

### Post by Mandarancid on 2008-05-05
Hi want to use kiba-dock but I have a problem after the installation when I run it works but all plugins (also icons list and louncher) don't works, the error is:

	For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:27675): WARNING **: Error (plugin-loader.c @ line 684):
	Failed to initiall plugin 'libwinlist.so': another plugin with the same name was initialled before!

Any help??

---

### Post by MongooseCage on 2008-05-05
> **Mandarancid said:**
> Hi want to use kiba-dock but I have a problem after the installation when I run it works but all plugins (also icons list and louncher) don't works, the error is:

	For a core dump, run kiba-dock with --g-fatal-warnings.

** (kiba-dock:27675): WARNING **: Error (plugin-loader.c @ line 684):
	Failed to initiall plugin 'libwinlist.so': another plugin with the same name was initialled before!

Any help??

If it's so much of a trouble why not try Avant Window Navigator, it may not seem as pretty or has all the physics but it's surely easy to install at least on Hardy. You can get it from the Add/Remove. Saved a lot of my troubles...

---

### Post by Mandarancid on 2008-05-05
> **MongooseCage said:**
> If it's so much of a trouble why not try Avant Window Navigator, it may not seem as pretty or has all the physics but it's surely easy to install at least on Hardy. You can get it from the Add/Remove. Saved a lot of my troubles...

I know but haven't a lot of the configuration that I want to do this: [http://mandarancio.deviantart.com/art/Concept-gnome-themes-2-84806365](http://mandarancio.deviantart.com/art/Concept-gnome-themes-2-84806365)

---

### Post by mattgaunt on 2008-05-05
unfortunately mandarancid kiba-dock is still in early stages, u could always post your problem in the kiba-dock forums, there is someone more likely to be able to help you than anyone here, i had a search on there but doesnt seem like anyone gets that error so I can't help sorry, all i can suggest is see if there is a libwinlist in synaptic package manager and if there is make sure you have the lib installed and the -dev version installed if its available

Gaunt

---

### Post by cloroxmartini on 2008-05-09
Alright, installed it and it works fine except for this...[IMG]http://img131.imageshack.us/img131/6771/screenshot1oi6.png[/IMG]

Any ideas?

---

### Post by talsemgeest on 2008-05-09
Make sure you have compositing enabled (eg compiz)

---

### Post by zenithlt on 2008-05-16
```
drm@drm:~/kiba-dock$ kiba-dock

** (process:21404): WARNING **: Error (main.c @ line 126):
	Failed to locate Plugins at '/usr/lib64/kiba-dock'
Please install the Plugins at '/usr/lib64/kiba-dock' or use the '--plugin-path' command line parameter.

	For a core dump, run kiba-dock with --g-fatal-warnings.

```

i`m getting this error

---

### Post by The Afterdark on 2008-05-22
Hi guys.  Maybe someone here can help me.

I didn't quite follow THIS how-to guide, I used the one here: [http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock](http://www.kiba-dock.org/components/com_mambowiki/index.php?title=Installing_Kiba-Dock)

I followed the instructions for Ubuntu 7.10, whereas I have 8.04.  I don't know how much of a difference that would make.

The thing is, it all installed just fine, and I got it working too.  However, when I go into the settings, and click on a button there, the whole window freezes up.

Has anyone else had this problem?  What could the cause of this problem be?  It'd be great if someone could help me out.

Thanks in advance.

---

### Post by mattgaunt on 2008-05-23
Those packages are built for Ubuntu 7.04 Im pretty sure that it would cause some problems being used for Herdy Heron. But I could be wrong about this.


Either way it could be the latest package loaded onto the repo is broken, unfortunately you'll have to wait for someone to fix the package and upload it.


You got to remember that kiba-dock isn't stable - I dont think any dock is, thats why none are included with ubuntu like compiz-fusion is.

You could try this how-to to get a kiba-dock version that you would be compiled to work with your machine, Im pretty sure this how-to would work with hardy heron altho I havent tried it so cant be certain, sorry

Gaunt

---

### Post by mattgaunt on 2008-05-23
Just a quick note, i just tried the how-to and everything worked without a problem for me on hardy heron

Just incase anyone reads this and is wondering

Gaunt

---

### Post by e2tango on 2008-05-27
I just installed on Hardy Heron with AMD64.

Worked fine for me :)
THANKS!
I'm a linux noob, just switched from XP and I have both installed at the moment.  Its been two weeks and I haven't booted into windows yet :D
I might have to at some point for a couple of little programs I couldn't get working in hardy heron.
This guide was very easy to follow, thanks :D

---

### Post by Watchtow3r on 2008-05-29
Has anyone got the akamaru physics engine working in hardy so that the icons bounce around? I dloaded kiba dock but the icons don't bounce around like that.Supposedly there was a problem about it a while back.

---

### Post by talsemgeest on 2008-05-30
Look back through the posts and you will find out how to do it...

---

### Post by vapotrini on 2008-05-31
> **Watchtow3r said:**
> Has anyone got the akamaru physics engine working in hardy so that the icons bounce around? I dloaded kiba dock but the icons don't bounce around like that.Supposedly there was a problem about it a while back.

Here it is again Kiba with physics, download and install, easy as pie...

[http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb](http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb)

---

### Post by maxfact on 2008-06-01
i have read into wiki kiba-dock on site official:
> For (optional) SVG support: cairo compiled with --enable-svg
this when and where to use

example:
kiba/akamaru$ ./autogen.sh --prefix=/usr --exec-prefix=/usr
--enable-svg
I must repeat for all briefcase download?
or enough only for akamuru o what briefcase downloaded :confused:

:lolflag:

---

### Post by HpZ on 2008-06-02
As soon as I enter the first line of code I get this:

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initialising package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

what the hell?

---

### Post by mattgaunt on 2008-06-02
All that means is that all the dependencies are already installed on your machine. Its fine

---

### Post by Watchtow3r on 2008-06-05
> **vapotrini said:**
> Here it is again Kiba with physics, download and install, easy as pie...

[http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb](http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb)

OK, I did that, now what?

---

### Post by vapotrini on 2008-06-05
> **Watchtow3r said:**
> OK, I did that, now what?

Double click the file and it'll install. 

Then simply go to, Applications>Accessories>Kiba-Dock

---

### Post by rated_emman on 2008-06-06
i tried to install kiba dock on my hardy heron but this is what i get


Code: 

emmanuel@emmanuel-laptop:~$ sudo aptitude remove automake1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
emmanuel@emmanuel-laptop:~$ sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-devmkdir kiba-dock
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
libcairo2 is already the newest version.
libgtop2-7 is already the newest version.
libgnomevfs2-0 is already the newest version.
libgnomeui-0 is already the newest version.
librsvg2-2 is already the newest version.
libgstreamer0.10-0 is already the newest version.
E: Couldn't find package libpurple-devmkdir
emmanuel@emmanuel-laptop:~$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/) akamaru
A    akamaru/include
A    akamaru/include/akamaru.h
A    akamaru/include/Makefile.am
A    akamaru/AUTHORS
A    akamaru/INSTALL
A    akamaru/configure.in
A    akamaru/ChangeLog
A    akamaru/akamaru.pc.in
A    akamaru/src
A    akamaru/src/akamaru.c
A    akamaru/src/Makefile.am
A    akamaru/COPYING
A    akamaru/Makefile.am
A    akamaru/autogen.sh
A    akamaru/NEWS
A    akamaru/README
Checked out revision 862.
emmanuel@emmanuel-laptop:~$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dock/) kiba-dock
A    kiba-dock/include
A    kiba-dock/include/kiba-drawable-object.h
A    kiba-dock/include/kiba-container-object.h
A    kiba-dock/include/kiba-icon.h
A    kiba-dock/include/kiba-cairo-utils.h
A    kiba-dock/include/kiba-desktop-editor.h
A    kiba-dock/include/kiba-win.h
A    kiba-dock/include/kiba-desktop-icon.h
A    kiba-dock/include/kiba-dialog.h
A    kiba-dock/include/kiba-utils.h
A    kiba-dock/include/kiba.h
A    kiba-dock/include/kiba-fixed-object.h
A    kiba-dock/include/kiba-progress.h
A    kiba-dock/include/kiba-types.h
A    kiba-dock/include/kiba-triangle.h
A    kiba-dock/include/kiba-object.h
A    kiba-dock/include/kiba-x11.h
A    kiba-dock/include/kiba-prefs-schema.h
A    kiba-dock/include/kiba-screen.h
A    kiba-dock/include/kiba-app-chooser.h
A    kiba-dock/include/kiba-dock.h
A    kiba-dock/include/kiba-title.h
A    kiba-dock/include/kiba-image.h
A    kiba-dock/include/kiba-info-win.h
A    kiba-dock/include/kiba-debug.h
A    kiba-dock/include/kiba-tooltip.h
A    kiba-dock/include/kiba-icon-view-win.h
A    kiba-dock/include/kiba-inline-pixbufs.h
A    kiba-dock/include/kiba-surface-factory.h
A    kiba-dock/include/kiba-plugin.h
A    kiba-dock/include/kiba-separator.h
A    kiba-dock/include/kiba-icon-view.h
A    kiba-dock/include/kiba-plugin-loader.h
A    kiba-dock/include/kiba-key-file.h
A    kiba-dock/include/kiba-window.h
A    kiba-dock/include/kiba-prefs.h
A    kiba-dock/include/Makefile.am
A    kiba-dock/include/kiba-menu-items.h
A    kiba-dock/include/kiba-globals.h
A    kiba-dock/include/kiba-macros.h
A    kiba-dock/VERSION
A    kiba-dock/AUTHORS
A    kiba-dock/ChangeLog
A    kiba-dock/src
A    kiba-dock/src/sdl-helper.c
A    kiba-dock/src/dialog.c
A    kiba-dock/src/desktop-icon.c
A    kiba-dock/src/utils.c
A    kiba-dock/src/separator-menu.c
A    kiba-dock/src/fixed-object.c
A    kiba-dock/src/sdl-helper.h
A    kiba-dock/src/marshallers.list
A    kiba-dock/src/separator-menu.h
A    kiba-dock/src/default-shape.c
A    kiba-dock/src/image.c
A    kiba-dock/src/kiba-private.h
A    kiba-dock/src/debug.c
A    kiba-dock/src/info-win.c
A    kiba-dock/src/default-shape.h
A    kiba-dock/src/tooltip.c
A    kiba-dock/src/podest-shape.c
A    kiba-dock/src/surface-factory.c
A    kiba-dock/src/dock-private.h
A    kiba-dock/src/title-private.h
A    kiba-dock/src/separator.c
A    kiba-dock/src/podest-shape.h
A    kiba-dock/src/prefs.c
A    kiba-dock/src/dock-menu.c
A    kiba-dock/src/container-object.c
A    kiba-dock/src/dock-menu.h
A    kiba-dock/src/prefs-dbus.xml
A    kiba-dock/src/icon.c
A    kiba-dock/src/prefs-callbacks.c
A    kiba-dock/src/prefs-callbacks.h
A    kiba-dock/src/progress.c
A    kiba-dock/src/triangle.c
A    kiba-dock/src/glitz-helper.c
A    kiba-dock/src/kiba.c
A    kiba-dock/src/object.c
A    kiba-dock/src/x11.c
A    kiba-dock/src/win-private.h
A    kiba-dock/src/dnd-window.c
A    kiba-dock/src/glitz-helper.h
A    kiba-dock/src/prefs-schema.c
A    kiba-dock/src/screen.c
A    kiba-dock/src/dnd-window.h
A    kiba-dock/src/dock.c
A    kiba-dock/src/app-chooser.c
A    kiba-dock/src/title.c
A    kiba-dock/src/startup-notification.c
A    kiba-dock/src/startup-notification.h
A    kiba-dock/src/icon-view-win.c
A    kiba-dock/src/plugin.c
A    kiba-dock/src/icon-view.c
A    kiba-dock/src/plugin-loader.c
A    kiba-dock/src/key-file.c
A    kiba-dock/src/window.c
A    kiba-dock/src/surface-factory-private.h
A    kiba-dock/src/prefs-dbus.c
A    kiba-dock/src/prefs-dbus.h
A    kiba-dock/src/menu-items.c
A    kiba-dock/src/main.c
A    kiba-dock/src/drawable-object.c
A    kiba-dock/src/Makefile.am
A    kiba-dock/src/cairo-utils.c
A    kiba-dock/src/prefs-private.h
A    kiba-dock/src/win.c
A    kiba-dock/src/desktop-editor.c
A    kiba-dock/kiba-dock.pc.in
A    kiba-dock/README
A    kiba-dock/files
A    kiba-dock/files/populate-dock.sh.in
A    kiba-dock/files/general.xml.in.in
A    kiba-dock/files/kiba-dock.desktop.in.in
A    kiba-dock/files/Makefile.am
A    kiba-dock/files/dock.xml.in.in
A    kiba-dock/configure.ac
A    kiba-dock/kiba-settings
A    kiba-dock/kiba-settings/kiba-gradient-chooser-dialog.c
A    kiba-dock/kiba-settings/settings-dbus.h
A    kiba-dock/kiba-settings/kiba-gradient-chooser.c
A    kiba-dock/kiba-settings/kiba-gradient-chooser-dialog.h
A    kiba-dock/kiba-settings/kiba-settings.c
A    kiba-dock/kiba-settings/kiba-settings.desktop.in.in
A    kiba-dock/kiba-settings/widgets.c
A    kiba-dock/kiba-settings/kiba-gradient-chooser.h
A    kiba-dock/kiba-settings/kiba-settings.h
A    kiba-dock/kiba-settings/widgets.h
A    kiba-dock/kiba-settings/settings-notebook.c
A    kiba-dock/kiba-settings/settings-notebook.h
A    kiba-dock/kiba-settings/settings-section-box.c
A    kiba-dock/kiba-settings/Makefile.am
A    kiba-dock/kiba-settings/settings-dbus.c
A    kiba-dock/kiba-settings/settings-section-box.h
A    kiba-dock/TODO
A    kiba-dock/INSTALL
A    kiba-dock/COPYING
A    kiba-dock/Makefile.am
A    kiba-dock/icons
A    kiba-dock/icons/kiba-dock-panel.svg
A    kiba-dock/icons/kiba_16.png
A    kiba-dock/icons/kiba-dock.svg
A    kiba-dock/icons/kiba_64.png
A    kiba-dock/icons/kiba_128.png
A    kiba-dock/icons/kiba_48.png
A    kiba-dock/icons/broken-glass.svg
A    kiba-dock/icons/Makefile.am
A    kiba-dock/icons/kiba-dock-objects.svg
A    kiba-dock/icons/kiba-window.svg
A    kiba-dock/icons/gear-dark.svg
A    kiba-dock/icons/gear.svg
A    kiba-dock/icons/kiba_24.png
A    kiba-dock/icons/visual-effects.svg
A    kiba-dock/autogen.sh
A    kiba-dock/NEWS
A    kiba-dock/po
A    kiba-dock/po/pt.po
A    kiba-dock/po/LINGUAS
A    kiba-dock/po/es.po
A    kiba-dock/po/fr.po
A    kiba-dock/po/bg.po
A    kiba-dock/po/de.po
A    kiba-dock/po/ChangeLog
A    kiba-dock/po/ja.po
A    kiba-dock/po/it.po
A    kiba-dock/po/POTFILES.in
Checked out revision 862.
emmanuel@emmanuel-laptop:~$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-plugins/) kiba-plugins
A    kiba-plugins/plugins
A    kiba-plugins/plugins/tray
A    kiba-plugins/plugins/tray/tray.c
A    kiba-plugins/plugins/tray/na-tray-manager.c
A    kiba-plugins/plugins/tray/tray.xml.in.in
A    kiba-plugins/plugins/tray/Makefile.am
A    kiba-plugins/plugins/tray/na-tray-manager.h
A    kiba-plugins/plugins/tray/na-marshal.list
A    kiba-plugins/plugins/akamaru
A    kiba-plugins/plugins/akamaru/akamaru.c
A    kiba-plugins/plugins/akamaru/kiba-akamaru.c
A    kiba-plugins/plugins/akamaru/Makefile.am
A    kiba-plugins/plugins/akamaru/kiba-akamaru.h
A    kiba-plugins/plugins/trash
A    kiba-plugins/plugins/trash/trash.c
A    kiba-plugins/plugins/trash/trash-monitor.c
A    kiba-plugins/plugins/trash/Makefile.am
A    kiba-plugins/plugins/trash/trash.xml.in.in
A    kiba-plugins/plugins/trash/trash-monitor.h
A    kiba-plugins/plugins/clipman
A    kiba-plugins/plugins/clipman/clipman.c
A    kiba-plugins/plugins/clipman/Makefile.am
A    kiba-plugins/plugins/clipman/clipman.xml.in.in
A    kiba-plugins/plugins/zoom
A    kiba-plugins/plugins/zoom/zoom.c
A    kiba-plugins/plugins/zoom/Makefile.am
A    kiba-plugins/plugins/zoom/zoom.xml.in.in
A    kiba-plugins/plugins/taskbar
A    kiba-plugins/plugins/taskbar/taskbar.xml.in.in
A    kiba-plugins/plugins/taskbar/taskbar.svg
A    kiba-plugins/plugins/taskbar/taskbar.c
A    kiba-plugins/plugins/taskbar/Makefile.am
A    kiba-plugins/plugins/marshallers.list
A    kiba-plugins/plugins/pulse
A    kiba-plugins/plugins/pulse/pulse.xml.in.in
A    kiba-plugins/plugins/pulse/Makefile.am
A    kiba-plugins/plugins/pulse/pulse.c
A    kiba-plugins/plugins/thumbnail-factory
A    kiba-plugins/plugins/thumbnail-factory/thumbnail-factory.xml.in.in
A    kiba-plugins/plugins/thumbnail-factory/Makefile.am
A    kiba-plugins/plugins/thumbnail-factory/thumbnail-factory.c
A    kiba-plugins/plugins/thumbnail-factory/thumbnail-dbus.xml
A    kiba-plugins/plugins/winlist
A    kiba-plugins/plugins/winlist/winlist.xml.in.in
A    kiba-plugins/plugins/winlist/Makefile.am
A    kiba-plugins/plugins/winlist/winlist.c
A    kiba-plugins/plugins/sysinfo
A    kiba-plugins/plugins/sysinfo/sysinfo_themes
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/custom_tango
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/custom_tango/sysinfo-frame.svg
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/custom_tango/sysinfo-hand.svg
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/custom_tango/sysinfo-face.svg
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/default
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/default/sysinfo-frame.svg
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/default/sysinfo-hand.svg
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/default/sysinfo-face.svg
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/gold
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/gold/sysinfo-frame.svg
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/gold/sysinfo-hand.svg
A    kiba-plugins/plugins/sysinfo/sysinfo_themes/gold/sysinfo-face.svg
A    kiba-plugins/plugins/sysinfo/sysinfo.xml.in.in
A    kiba-plugins/plugins/sysinfo/Makefile.am
A    kiba-plugins/plugins/sysinfo/sysinfo.c
A    kiba-plugins/plugins/clock
A    kiba-plugins/plugins/clock/calendar.h
A    kiba-plugins/plugins/clock/clock.xml.in.in
A    kiba-plugins/plugins/clock/Makefile.am
A    kiba-plugins/plugins/clock/calendar.c
A    kiba-plugins/plugins/clock/clock.c
A    kiba-plugins/plugins/clock/clock_theme
A    kiba-plugins/plugins/clock/clock_theme/clock-hour-hand-shadow.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-glass.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-minute-hand.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-frame.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-minute-hand-shadow.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-marks.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-face.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-face-shadow.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-second-hand.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-hour-hand.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-second-hand-shadow.svg
A    kiba-plugins/plugins/clock/clock_theme/clock-drop-shadow.svg
A    kiba-plugins/plugins/dbus
A    kiba-plugins/plugins/dbus/dbus.png
A    kiba-plugins/plugins/dbus/kiba-dbus.xml
A    kiba-plugins/plugins/dbus/dbus.xml.in.in
A    kiba-plugins/plugins/dbus/Makefile.am
A    kiba-plugins/plugins/dbus/dbus.c
A    kiba-plugins/plugins/rotate
A    kiba-plugins/plugins/rotate/rotate.c
A    kiba-plugins/plugins/rotate/rotate.xml.in.in
A    kiba-plugins/plugins/rotate/Makefile.am
A    kiba-plugins/plugins/switch
A    kiba-plugins/plugins/switch/switch.c
A    kiba-plugins/plugins/switch/Makefile.am
A    kiba-plugins/plugins/switch/switch.xml.in.in
A    kiba-plugins/plugins/launcher
A    kiba-plugins/plugins/launcher/launcher.c
A    kiba-plugins/plugins/launcher/launcher.h
A    kiba-plugins/plugins/launcher/Makefile.am
A    kiba-plugins/plugins/launcher/launcher.xml.in.in
A    kiba-plugins/plugins/launcher/launcher-plugin.c
A    kiba-plugins/plugins/stack
A    kiba-plugins/plugins/stack/stack-file-property-window.h
A    kiba-plugins/plugins/stack/stack-icon.h
A    kiba-plugins/plugins/stack/kiba-mime-application-chooser.h
A    kiba-plugins/plugins/stack/stack-plugin.c
A    kiba-plugins/plugins/stack/stack-icon-view.c
A    kiba-plugins/plugins/stack/stack.c
A    kiba-plugins/plugins/stack/Makefile.am
A    kiba-plugins/plugins/stack/kiba-mime-extensions.c
A    kiba-plugins/plugins/stack/stack-icon-view.h
A    kiba-plugins/plugins/stack/stack-file-property-window.c
A    kiba-plugins/plugins/stack/stack.h
A    kiba-plugins/plugins/stack/stack-icon.c
A    kiba-plugins/plugins/stack/kiba-mime-application-chooser.c
A    kiba-plugins/plugins/stack/kiba-mime-extensions.h
A    kiba-plugins/plugins/stack/stack.xml.in.in
A    kiba-plugins/plugins/volume
A    kiba-plugins/plugins/volume/volume.xml.in.in
A    kiba-plugins/plugins/volume/gst_mixer.c
A    kiba-plugins/plugins/volume/alsa_mixer.c
A    kiba-plugins/plugins/volume/mixer.c
A    kiba-plugins/plugins/volume/gst_mixer.h
A    kiba-plugins/plugins/volume/volume.c
A    kiba-plugins/plugins/volume/Makefile.am
A    kiba-plugins/plugins/volume/alsa_mixer.h
A    kiba-plugins/plugins/volume/mixer.h
A    kiba-plugins/plugins/Makefile.am
A    kiba-plugins/plugins/gnome-applets
A    kiba-plugins/plugins/gnome-applets/gnome-applets.xml.in.in
A    kiba-plugins/plugins/gnome-applets/KIBA_Panel_Popup.xml
A    kiba-plugins/plugins/gnome-applets/Makefile.am
A    kiba-plugins/plugins/gnome-applets/gnome-applet-chooser.c
A    kiba-plugins/plugins/gnome-applets/gnome-applets.c
A    kiba-plugins/plugins/gnome-applets/gnome-applet-chooser.h
A    kiba-plugins/plugins/gmenu
A    kiba-plugins/plugins/gmenu/gmenu.xml.in.in
A    kiba-plugins/plugins/gmenu/gmenu-dbus.xml
A    kiba-plugins/plugins/gmenu/Makefile.am
A    kiba-plugins/plugins/gmenu/gmenu.c
A    kiba-plugins/plugins/bounce
A    kiba-plugins/plugins/bounce/bounce.xml.in.in
A    kiba-plugins/plugins/bounce/Makefile.am
A    kiba-plugins/plugins/bounce/bounce.c
A    kiba-plugins/AUTHORS
A    kiba-plugins/TODO
A    kiba-plugins/INSTALL
A    kiba-plugins/configure.in
A    kiba-plugins/ChangeLog
A    kiba-plugins/COPYING
A    kiba-plugins/Makefile.am
A    kiba-plugins/autogen.sh
A    kiba-plugins/NEWS
A    kiba-plugins/README
A    kiba-plugins/po
A    kiba-plugins/po/pt.po
A    kiba-plugins/po/LINGUAS
A    kiba-plugins/po/es.po
A    kiba-plugins/po/fr.po
A    kiba-plugins/po/bg.po
A    kiba-plugins/po/de.po
A    kiba-plugins/po/ChangeLog
A    kiba-plugins/po/ja.po
A    kiba-plugins/po/it.po
A    kiba-plugins/po/POTFILES.in
Checked out revision 862.
emmanuel@emmanuel-laptop:~$ svn co [https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/](https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/kiba-dbus-plugins/) kiba-dbus-plugins
A    kiba-dbus-plugins/configure.ac
A    kiba-dbus-plugins/AUTHORS
A    kiba-dbus-plugins/TODO
A    kiba-dbus-plugins/VERSION
A    kiba-dbus-plugins/themes
A    kiba-dbus-plugins/themes/kiba-signal
A    kiba-dbus-plugins/themes/kiba-signal/0.png
A    kiba-dbus-plugins/themes/kiba-signal/100.png
A    kiba-dbus-plugins/themes/kiba-signal/20.png
A    kiba-dbus-plugins/themes/kiba-signal/40.png
A    kiba-dbus-plugins/themes/kiba-signal/60.png
A    kiba-dbus-plugins/themes/kiba-signal/80.png
A    kiba-dbus-plugins/themes/kiba-weather
A    kiba-dbus-plugins/themes/kiba-weather/nightcloud.png
A    kiba-dbus-plugins/themes/kiba-weather/nightsnow.png
A    kiba-dbus-plugins/themes/kiba-weather/raincloud.png
A    kiba-dbus-plugins/themes/kiba-weather/Copyright.txt
A    kiba-dbus-plugins/themes/kiba-weather/nightrain.png
A    kiba-dbus-plugins/themes/kiba-weather/daycloud.png
A    kiba-dbus-plugins/themes/kiba-weather/daysnow.png
A    kiba-dbus-plugins/themes/kiba-weather/nightfog.png
A    kiba-dbus-plugins/themes/kiba-weather/sun.png
A    kiba-dbus-plugins/themes/kiba-weather/cloud.png
A    kiba-dbus-plugins/themes/kiba-weather/snow.png
A    kiba-dbus-plugins/themes/kiba-weather/dayrain.png
A    kiba-dbus-plugins/themes/kiba-weather/moon.png
A    kiba-dbus-plugins/themes/kiba-weather/dayfog.png
A    kiba-dbus-plugins/themes/kiba-weather/fog.png
A    kiba-dbus-plugins/themes/kiba-mail
A    kiba-dbus-plugins/themes/kiba-mail/none.png
A    kiba-dbus-plugins/themes/kiba-mail/AUTHORS
A    kiba-dbus-plugins/themes/kiba-mail/new.png
A    kiba-dbus-plugins/themes/Makefile.am
A    kiba-dbus-plugins/themes/kiba-battery
A    kiba-dbus-plugins/themes/kiba-battery/0.png
A    kiba-dbus-plugins/themes/kiba-battery/none.png
A    kiba-dbus-plugins/themes/kiba-battery/100.png
A    kiba-dbus-plugins/themes/kiba-battery/50.png
A    kiba-dbus-plugins/themes/kiba-battery/25.png
A    kiba-dbus-plugins/themes/kiba-battery/75.png
A    kiba-dbus-plugins/themes/kiba-feeder
A    kiba-dbus-plugins/themes/kiba-feeder/old.png
A    kiba-dbus-plugins/themes/kiba-feeder/new.png
A    kiba-dbus-plugins/INSTALL
A    kiba-dbus-plugins/ChangeLog
A    kiba-dbus-plugins/scripts
A    kiba-dbus-plugins/scripts/kiba-weather.py.in
A    kiba-dbus-plugins/scripts/quod_dbus_cover.py.in
A    kiba-dbus-plugins/scripts/kiba-mail.py.in
A    kiba-dbus-plugins/scripts/Makefile.am
A    kiba-dbus-plugins/scripts/kiba-amarok.py.in
A    kiba-dbus-plugins/scripts/kiba-battery.py.in
A    kiba-dbus-plugins/scripts/kiba-feeder.py.in
A    kiba-dbus-plugins/scripts/kiba-signal.py.in
A    kiba-dbus-plugins/scripts/firefox.py.in
A    kiba-dbus-plugins/COPYING
A    kiba-dbus-plugins/Makefile.am
A    kiba-dbus-plugins/data
A    kiba-dbus-plugins/data/python_scripts.xml.in.in
A    kiba-dbus-plugins/data/kiba-amarok.spec
A    kiba-dbus-plugins/data/Makefile.am
A    kiba-dbus-plugins/autogen.sh
A    kiba-dbus-plugins/NEWS
A    kiba-dbus-plugins/README
A    kiba-dbus-plugins/po
A    kiba-dbus-plugins/po/pt.po
A    kiba-dbus-plugins/po/LINGUAS
A    kiba-dbus-plugins/po/es.po
A    kiba-dbus-plugins/po/bg.po
A    kiba-dbus-plugins/po/de.po
A    kiba-dbus-plugins/po/ja.po
A    kiba-dbus-plugins/po/it.po
A    kiba-dbus-plugins/po/POTFILES.in
Checked out revision 862.
emmanuel@emmanuel-laptop:~$ kiba-dock
bash: kiba-dock: command not found
emmanuel@emmanuel-laptop:~$ cd akamaru/
emmanuel@emmanuel-laptop:~/akamaru$ ./autogen.sh --prefix=/usr --exec-prefix=/usr

checking for intltool...
***Error***: You must have intltool installed to compile akamaru
emmanuel@emmanuel-laptop:~/akamaru$ sudo make install
make: *** No rule to make target `install'.  Stop.
emmanuel@emmanuel-laptop:~/akamaru$ cd ..

can anybody help?

---

### Post by Gourgi on 2008-06-06
try this
```
sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev intltool intltool-debian
```
then just start over the process : 
```

svn co https://kibadock.svn.sourceforge.net/svnroot/kibadock/trunk/akamaru/ akamaru

``` and the others

---

### Post by mattgaunt on 2008-06-06
> emmanuel@emmanuel-laptop:~$ sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-devmkdir kiba-dock

if u look at the end you accidentally joined the two seperate commands to type into the terminal it should be

$ sudo apt-get install fakeroot automake1.9 build-essential libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx1-dev librsvg2-dev libglade2-dev libxcomposite-dev subversion libtool libgtop2-dev python-gtk2-dev libgnome-menu-dev libgnomeui-dev libgnomevfs2-dev intltool libxml2-dev libglitz1-dev libcairo2 libdbus-1-dev libgtop2-7 libgnomevfs2-0 libgnomeui-0 librsvg2-2 python-feedparser libasound2-dev libsdl1.2-dev libdbus-glib-1-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgstreamer0.10-0 pidgin-dev libpurple-dev

and then

mkdir kiba-dock

You'll have to repeat the how-to to get it working again just like Gourgi said in the previous reply

Gaunt

---

### Post by rated_emman on 2008-06-06
hey guys... i actually did what u told me to do.. here is the hole process

[PHP]checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
./configure: line 22470: ./po/POTFILES.in: No such file or directory
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for sqrt... no
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for AKAMARU... yes
checking for GLIB... yes
configure: creating ./config.status
config.status: creating akamaru.pc
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
Now type `make' to compile akamaru
emmanuel@emmanuel-laptop:~/kiba-dock/akamaru$ sudo make install 
Making install in src
make[1]: Entering directory `/home/emmanuel/kiba-dock/akamaru/src'
make[2]: Entering directory `/home/emmanuel/kiba-dock/akamaru/src'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libakamaru.la' '/usr/local/lib/libakamaru.la'
/usr/bin/install -c .libs/libakamaru.so.0.0.0 /usr/local/lib/libakamaru.so.0.0.0
(cd /usr/local/lib && { ln -s -f libakamaru.so.0.0.0 libakamaru.so.0 || { rm -f libakamaru.so.0 && ln -s libakamaru.so.0.0.0 libakamaru.so.0; }; })
(cd /usr/local/lib && { ln -s -f libakamaru.so.0.0.0 libakamaru.so || { rm -f libakamaru.so && ln -s libakamaru.so.0.0.0 libakamaru.so; }; })
/usr/bin/install -c .libs/libakamaru.lai /usr/local/lib/libakamaru.la
/usr/bin/install -c .libs/libakamaru.a /usr/local/lib/libakamaru.a
chmod 644 /usr/local/lib/libakamaru.a
ranlib /usr/local/lib/libakamaru.a
libtool: install: warning: remember to run `libtool --finish /usr/lib'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/src'
make[1]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/src'
Making install in include
make[1]: Entering directory `/home/emmanuel/kiba-dock/akamaru/include'
make[2]: Entering directory `/home/emmanuel/kiba-dock/akamaru/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/akamaru" || mkdir -p -- "/usr/local/include/akamaru"
 /usr/bin/install -c -m 644 'akamaru.h' '/usr/local/include/akamaru/akamaru.h'
make[2]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/include'
make[1]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/include'
make[1]: Entering directory `/home/emmanuel/kiba-dock/akamaru'
make[2]: Entering directory `/home/emmanuel/kiba-dock/akamaru'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pkgconfig" || mkdir -p -- "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'akamaru.pc' '/usr/local/lib/pkgconfig/akamaru.pc'
make[2]: Leaving directory `/home/emmanuel/kiba-dock/akamaru'
make[1]: Leaving directory `/home/emmanuel/kiba-dock/akamaru'
emmanuel@emmanuel-laptop:~/kiba-dock/akamaru$ cd ..cd kiba-plugins/
bash: cd: ..cd: No such file or directory
emmanuel@emmanuel-laptop:~/kiba-dock/akamaru$ ./autogen.sh

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy
Putting files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'

Running './configure ' ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
./configure: line 22470: ./po/POTFILES.in: No such file or directory
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for sqrt... no
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for AKAMARU... yes
checking for GLIB... yes
configure: creating ./config.status
config.status: creating akamaru.pc
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
Now type `make' to compile akamaru
emmanuel@emmanuel-laptop:~/kiba-dock/akamaru$ sudo make install 
Making install in src
make[1]: Entering directory `/home/emmanuel/kiba-dock/akamaru/src'
make[2]: Entering directory `/home/emmanuel/kiba-dock/akamaru/src'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libakamaru.la' '/usr/local/lib/libakamaru.la'
/usr/bin/install -c .libs/libakamaru.so.0.0.0 /usr/local/lib/libakamaru.so.0.0.0
(cd /usr/local/lib && { ln -s -f libakamaru.so.0.0.0 libakamaru.so.0 || { rm -f libakamaru.so.0 && ln -s libakamaru.so.0.0.0 libakamaru.so.0; }; })
(cd /usr/local/lib && { ln -s -f libakamaru.so.0.0.0 libakamaru.so || { rm -f libakamaru.so && ln -s libakamaru.so.0.0.0 libakamaru.so; }; })
/usr/bin/install -c .libs/libakamaru.lai /usr/local/lib/libakamaru.la
/usr/bin/install -c .libs/libakamaru.a /usr/local/lib/libakamaru.a
chmod 644 /usr/local/lib/libakamaru.a
ranlib /usr/local/lib/libakamaru.a
libtool: install: warning: remember to run `libtool --finish /usr/lib'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/src'
make[1]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/src'
Making install in include
make[1]: Entering directory `/home/emmanuel/kiba-dock/akamaru/include'
make[2]: Entering directory `/home/emmanuel/kiba-dock/akamaru/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/akamaru" || mkdir -p -- "/usr/local/include/akamaru"
 /usr/bin/install -c -m 644 'akamaru.h' '/usr/local/include/akamaru/akamaru.h'
make[2]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/include'
make[1]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/include'
make[1]: Entering directory `/home/emmanuel/kiba-dock/akamaru'
make[2]: Entering directory `/home/emmanuel/kiba-dock/akamaru'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pkgconfig" || mkdir -p -- "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'akamaru.pc' '/usr/local/lib/pkgconfig/akamaru.pc'
make[2]: Leaving directory `/home/emmanuel/kiba-dock/akamaru'
make[1]: Leaving directory `/home/emmanuel/kiba-dock/akamaru'
emmanuel@emmanuel-laptop:~/kiba-dock/akamaru$ cd ..cd kiba-dbus-plugins/
bash: cd: ..cd: No such file or directory
emmanuel@emmanuel-laptop:~/kiba-dock/akamaru$ ./autogen.sh

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal 
autoreconf: configure.in: tracing
autoreconf: running: libtoolize --copy
Putting files in AC_CONFIG_AUX_DIR, `config'.
libtoolize: `config.guess' exists: use `--force' to overwrite
libtoolize: `config.sub' exists: use `--force' to overwrite
libtoolize: `ltmain.sh' exists: use `--force' to overwrite
autoreconf: running: /usr/bin/autoconf
autoreconf: running: /usr/bin/autoheader
autoreconf: running: automake --add-missing --copy --no-force
autoreconf: Leaving directory `.'

Running './configure ' ...
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognize dependent libraries... pass_all
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for xlf... no
checking for f77... no
checking for frt... no
checking for pgf77... no
checking for cf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for xlf90... no
checking for f90... no
checking for pgf90... no
checking for pghpf... no
checking for epcf90... no
checking for gfortran... no
checking for g95... no
checking for xlf95... no
checking for f95... no
checking for fort... no
checking for ifort... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for ftn... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 98304
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
(cached) (cached) checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ANSI C header files... (cached) yes
checking for stdlib.h... (cached) yes
checking for string.h... (cached) yes
checking locale.h usability... yes
checking locale.h presence... yes
checking for locale.h... yes
checking for LC_MESSAGES... yes
checking libintl.h usability... yes
checking libintl.h presence... yes
checking for libintl.h... yes
checking for ngettext in libc... yes
checking for dgettext in libc... yes
checking for bind_textdomain_codeset... yes
checking for msgfmt... /usr/bin/msgfmt
checking for dcgettext... yes
checking if msgfmt accepts -c... yes
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
./configure: line 22470: ./po/POTFILES.in: No such file or directory
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking for size_t... yes
checking whether time.h and sys/time.h may both be included... yes
checking for stdbool.h that conforms to C99... yes
checking for _Bool... yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for sqrt... no
checking whether byte ordering is bigendian... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for AKAMARU... yes
checking for GLIB... yes
configure: creating ./config.status
config.status: creating akamaru.pc
config.status: creating Makefile
config.status: creating include/Makefile
config.status: creating src/Makefile
config.status: creating config.h
config.status: config.h is unchanged
config.status: executing depfiles commands
config.status: executing default-1 commands
Now type `make' to compile akamaru
emmanuel@emmanuel-laptop:~/kiba-dock/akamaru$ sudo make install
Making install in src
make[1]: Entering directory `/home/emmanuel/kiba-dock/akamaru/src'
make[2]: Entering directory `/home/emmanuel/kiba-dock/akamaru/src'
test -z "/usr/local/lib" || mkdir -p -- "/usr/local/lib"
 /bin/bash ../libtool --mode=install /usr/bin/install -c  'libakamaru.la' '/usr/local/lib/libakamaru.la'
/usr/bin/install -c .libs/libakamaru.so.0.0.0 /usr/local/lib/libakamaru.so.0.0.0
(cd /usr/local/lib && { ln -s -f libakamaru.so.0.0.0 libakamaru.so.0 || { rm -f libakamaru.so.0 && ln -s libakamaru.so.0.0.0 libakamaru.so.0; }; })
(cd /usr/local/lib && { ln -s -f libakamaru.so.0.0.0 libakamaru.so || { rm -f libakamaru.so && ln -s libakamaru.so.0.0.0 libakamaru.so; }; })
/usr/bin/install -c .libs/libakamaru.lai /usr/local/lib/libakamaru.la
/usr/bin/install -c .libs/libakamaru.a /usr/local/lib/libakamaru.a
chmod 644 /usr/local/lib/libakamaru.a
ranlib /usr/local/lib/libakamaru.a
libtool: install: warning: remember to run `libtool --finish /usr/lib'
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/src'
make[1]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/src'
Making install in include
make[1]: Entering directory `/home/emmanuel/kiba-dock/akamaru/include'
make[2]: Entering directory `/home/emmanuel/kiba-dock/akamaru/include'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/include/akamaru" || mkdir -p -- "/usr/local/include/akamaru"
 /usr/bin/install -c -m 644 'akamaru.h' '/usr/local/include/akamaru/akamaru.h'
make[2]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/include'
make[1]: Leaving directory `/home/emmanuel/kiba-dock/akamaru/include'
make[1]: Entering directory `/home/emmanuel/kiba-dock/akamaru'
make[2]: Entering directory `/home/emmanuel/kiba-dock/akamaru'
make[2]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/lib/pkgconfig" || mkdir -p -- "/usr/local/lib/pkgconfig"
 /usr/bin/install -c -m 644 'akamaru.pc' '/usr/local/lib/pkgconfig/akamaru.pc'
make[2]: Leaving directory `/home/emmanuel/kiba-dock/akamaru'
make[1]: Leaving directory `/home/emmanuel/kiba-dock/akamaru'[/PHP]

but when i try to run it, it gives me this: :(

[PHP]emmanuel@emmanuel-laptop:~$ kiba-dock
bash: kiba-dock: command not found
emmanuel@emmanuel-laptop:~$ [/PHP]

i dunno what to do... plzz helpp

---

### Post by Gourgi on 2008-06-06
emmanuel@emmanuel-laptop:~/kiba-dock/akamaru$ [COLOR="Red"]cd ..cd kiba-plugins/[/COLOR]this command is wrong, i should be 
```

cd ..
cd kiba-plugins/

```there is an error after this line
try to start again from beginning and pay attention on what you type and on what the output of terminal says.
i know you may not understand the hole output but if an error occurs, i 'm sure you'll notice it

---

### Post by rated_emman on 2008-06-06
thank you sooo much you guys!!! i finally installed it!!!!!

but i just got one more problem :s

whenever i close the terminal, it closes the kiba-dock as well!

thank you in advance

---

### Post by talsemgeest on 2008-06-06
Yeah, thats with any program you run from the terminal.

Easy to fix though. Just type <alt> + <F2>, then type in kiba-dock. That will also work with any other program you want to run.

Hope this helps :)

---

### Post by Watchtow3r on 2008-06-06
> **vapotrini said:**
> Double click the file and it'll install. 

Then simply go to, Applications>Accessories>Kiba-Dock

Ok, I did THAT, now what? (see where I'm going with this?)

---

### Post by mattgaunt on 2008-06-07
Watchtower your really not helping anyone fix your problem, simply saying what do i do now? doesnt explain where ur going wrong.

When you go to applications->Accessories->Kiba-Dock the dock should appear at the bottom of your screen, are you sayin its not coming up on your screen?

Gaunt

---

### Post by rated_emman on 2008-06-07
hey there linux experts.. uhm i just got a few questions...

i installed kiba-dock and correctly running it... i added a new launcher (firefox) and whenever i click it, it opens a window but it says cannot load the page or something... but when i launch it from the panel, it works fine... 

when i have the firefox open already, i try to open another window and it just opens a new tab with loading error as well....

-------------------------------------------------------------------------

when i open firefox, it opens another icon on the right side of the dock... but when i have two firefox windows opened, it stays as one icon... is there anyway i can fix that? 


thank you guys soo much in advance :D

---

### Post by vapotrini on 2008-06-07
> **rated_emman said:**
> hey there linux experts.. uhm i just got a few questions...

i installed kiba-dock and correctly running it... i added a new launcher (firefox) and whenever i click it, it opens a window but it says cannot load the page or something... but when i launch it from the panel, it works fine... 

when i have the firefox open already, i try to open another window and it just opens a new tab with loading error as well....

-------------------------------------------------------------------------

when i open firefox, it opens another icon on the right side of the dock... but when i have two firefox windows opened, it stays as one icon... is there anyway i can fix that? 


thank you guys soo much in advance :D

Right click on the launcher firefox, then go into it's properties, then click on launcher and change command to: firefox %u

---

### Post by rated_emman on 2008-06-07
is it also possible to have one icon on the dock per every window that you open?

coz when i open multiple firefox, the icon on the dock stays as one only

---

### Post by talsemgeest on 2008-06-08
You just right click the icon and choose which window you want

---

### Post by rated_emman on 2008-06-10
how do you guys make the kiba dock behave like it's bouncing around and stuff? i can't seem to figure out how to make it behave just like that

thank you

---

### Post by talsemgeest on 2008-06-10
Please read the whole thread before asking questions. The answer is a few pages back. Basically you need to download the svn, then downgrade that to a previous version that still had the physics. Then you build it like you normally would.

---

### Post by rated_emman on 2008-06-10
> **vapotrini said:**
> Here it is again Kiba with physics, download and install, easy as pie...

[http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb](http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb)

i downloaded and installed it, how do i configure it?

thanks in advance

---

### Post by Watchtow3r on 2008-06-10
is that post by vapotrini the whole kiba-dock with physics, or just the part that enables the physics? Because I think my problem is that I still have the newest version, so I would need to uninstall it, install an older version, then install the thing in Vapotrini's post? Or do I just uninstall it, then install the thing in his post?

---

### Post by talsemgeest on 2008-06-11
> **Watchtow3r said:**
> is that post by vapotrini the whole kiba-dock with physics, or just the part that enables the physics? Because I think my problem is that I still have the newest version, so I would need to uninstall it, install an older version, then install the thing in Vapotrini's post? Or do I just uninstall it, then install the thing in his post?
Wait, what version do you have installed now? Svn or deb?

---

### Post by rated_emman on 2008-06-11
> **talsemgeest said:**
> Wait, what version do you have installed now? Svn or deb?

i know ur not asking me but i got the same question... coz i installed that deb thingy and nothing happened to my kiba dock...

how to do downgrade? do i uninstall my current dock? how do i install the svn? or what is svn?

im soo sorry im very new to this things

i really appreciate all you guy's help.. thank you so much

---

### Post by talsemgeest on 2008-06-11
Ah, it's no problem, I hope I can help you.

Svn lets you download the latest (and buggiest) version of a program. In this case, Kiba-dock.

To find out how to install it from the svn, just go back to the first page of this thread.

After you have done that (which I think you have already done), you have the latest version of Kiba-dock. But unfortunately, this has absolutely no physics.

Give me a few minutes and I will try and find the command needed to downgrade, and which version you need to downgrade to.

---

### Post by talsemgeest on 2008-06-11
Ok, run the following commands if you have all ready gone through Mattgaunts original post:
```

cd kiba-dock
svn update -r 602 *
```

And then do the rest of the commands again from where it says "32 bit Ubuntu users" if you are using 32 bit, and "64 bit Ubuntu users" if you are using 64 bit.

Also, if Mattgaunt is reading this, would you mind putting this command into the original post?

---

### Post by rated_emman on 2008-06-11
> **talsemgeest said:**
> Ok, run the following commands if you have all ready gone through Mattgaunts original post:
```

cd kiba-dock
svn update -r 602 *
```

And then do the rest of the commands again from where it says "32 bit Ubuntu users" if you are using 32 bit, and "64 bit Ubuntu users" if you are using 64 bit.

Also, if Mattgaunt is reading this, would you mind putting this command into the original post?

here's what i get:

```
emman@emmanuel-laptop:~$ cd kiba-dock
bash: cd: kiba-dock: No such file or directory
emman@emmanuel-laptop:~$ svn update -r 602 *
Skipped 'Desktop'
Skipped 'Documents'
Skipped 'Examples'
Skipped 'Music'
Skipped 'Pictures'
Skipped 'Public'
Skipped 'Templates'
Skipped 'Videos'
emman@emmanuel-laptop:~$ 

```

and sorry.. what you mean put this code on the original post?

im sorry if im such a real pain :S

and thank you so much for u patience

---

### Post by talsemgeest on 2008-06-11
Ok, so have you allready done all of the instructions on the first page? As in this one: [http://ubuntuforums.org/showpost.php?p=3386853&postcount=1](http://ubuntuforums.org/showpost.php?p=3386853&postcount=1)

By the way, the last line of my last post was meant for mattgaunt, the creator of this how-to.

---

### Post by rated_emman on 2008-06-11
I mean yeah ive done it b4 wen i 1st installed kiba. So u mean i have 2 do it all again? (sorry 4 misunderstanding) 

And i dont have 2 do any uninstallation ryt?

Thanx much again :D

---

### Post by talsemgeest on 2008-06-11
No, you shouldn't have to. The command I made assumes that you have downloaded all of the svn files into the kiba-dock folder.

Just have a look around in your home folder for a folder that relates to kiba dock, then tell me what it is. If you can't find anything, just start from the beginning of the guide, making sure to do absolutely everything it says down to the word.

---

### Post by rated_emman on 2008-06-11
i looked into my home folder and i couldn't find the folder with kiba's... i just remembered that i deleted the last user i was in when i installed the first kiba dock... (but im still able to use and run the newest kiba dock after i deleted that user).... so i just did the step-by-step guide from mattgaunt...

after i made the directory, as said in the HOW TO: by mattgaunt, i copy and paste the command that u provided earlier...

```
cd kiba-dock
svn update -r 602 *
```

then i followed the rest of the codes for the 32-bit user...
... as far as i know of, it finished installing... 

so i go back to the terminal and input

```
kiba-dock
```

to launch the application...but i get this error msg:

```
emman@emmanuel-laptop:~$ kiba-dock
** Message: cant load file '/home/emman/.kiba-dock/config': Error reading file '/home/emman/.kiba-dock/config': Is a directory

** (kiba-dock:20048): WARNING **: Error (main.c @ line 252):
	Failed to locate Plugins at '/usr/lib/kiba-dock'
Please install the Plugins at '/usr/lib/kiba-dock' or use the '--plugin-path' command line parameter.

```

and it wont start the program....
i tried going to application>accessories>Kiba-dock but it wont load also
then i tried to go to the kiba dock settings, and this is what i see:

[IMG]http://i16.photobucket.com/albums/b39/emman121789/Screenshot.png[/IMG]

which im pretty sure has different options than the one i've installed before (the newest one before i did the code that u gave me talsemgeest..

Once again, thanks for all the help and patience :D

---

### Post by talsemgeest on 2008-06-11
Ok, now this is beyond me. I think I might try to install it too.

I know what the error message means, but I don't know how to fix it. If you followed the guide...

Sorry I can't be of more help :(

---

### Post by rated_emman on 2008-06-11
uhm i uninstalled it and re-install the 602 version.. i actually got it working but when i tried to drag the icon, it wont start... hmppp weird...

i try to run it in terminal using code: kiba-dock and this is the error that i get:

```
emman@emmanuel-laptop:~$ kiba-dock
** Message: error parsing desktop file for /apps/kiba/launchers/Screen: /home/emman/.kiba-dock/Screenshot.png is not a .desktop file

** Message: error parsing desktop file for /apps/kiba/launchers/D: /home/emman/.kiba-dock/Documents is not a .desktop file

** Message: found unused desktop file in homdir
try to merge /home/emman/.kiba-dock/Pictures to gconf

** Message: Failed to merge unused desktop file /home/emman/.kiba-dock/Pictures. notifications: Bad key or directory name: "/apps/kiba/launchers//file": Can't have two slashes '/' in a row

(kiba-dock:6430): GConf-CRITICAL **: gconf_client_get_string: assertion `err == NULL || *err == NULL' failed
** Message: found unused desktop file in homdir
try to merge /home/emman/.kiba-dock/Screenshot.png to gconf

Floating point exception

```

---

### Post by talsemgeest on 2008-06-12
Well I would have suggested making sure you have all of your graphics configured properly, but I see you have compiz running which means all of that is working.

Other than that I have no idea. Sorry :(

---

### Post by rated_emman on 2008-06-12
heheh no bad feelings :D u did everything you could to help me :D

and btw i think i'll just install the latest one... so do i just have to run the HOW TO again? or do i have to uninstall it?

if i do have to uninstall it first, how to? i know it says on the first page how but it's confusing for me, do i rename the folder? or i dunno what it means :-s 

thanks again

---

### Post by talsemgeest on 2008-06-12
Nah, you should just be able to install over the top. That's how it has always worked for me.

---

### Post by vapotrini on 2008-06-12
> **rated_emman said:**
> i downloaded and installed it, how do i configure it?

thanks in advance


Right click on the dock and go into: Kiba-Utils>gset-kiba

---

### Post by vapotrini on 2008-06-12
> **Watchtow3r said:**
> is that post by vapotrini the whole kiba-dock with physics, or just the part that enables the physics? Because I think my problem is that I still have the newest version, so I would need to uninstall it, install an older version, then install the thing in Vapotrini's post? Or do I just uninstall it, then install the thing in his post?

Yes, I do believe you're gonna have to uninstall the latest version for the one I posted to work. Think you're gonna have to remove it completely but I'm not 100%. 

The one I posted is the whole kiba-dock with physics, it's just an older verison. It doesn't have as many features as the latest kiba but IMO the physics just can't be beat. Besides, it's so much easier to install, simply download and double click to install... the end.

[http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb](http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb)

---

### Post by mattgaunt on 2008-06-12
Hey guys

Just to let you know ill put up the extra bit regarding the physics engine version hopefully later tonight or 2moro.

Apologies for the late reply, bn at a festival for past cpl of days

Gaunt

---

### Post by Zero_Cool on 2008-06-12
after i do
[B] "cd akamaru/
./autogen.sh --prefix=/usr --exec-prefix=/usr
sudo make install
cd .." [/B]
    nothing else seems to want to install and says unknown file name.

---

### Post by Watchtow3r on 2008-06-13
I tried to uninstall kiba-dock but it didn't work. For one thing, I'm pretty sure that where it says "cd.." it should be "cd .." (note the space). Also, upon doing all the steps (using cd .. rather than cd..), under Applications in Accesories I still have the Kiba-dock icon, and when I click it it shows a little wierd small kiba-dock with no icons in it. Also, I went to Synaptic, then searched Kiba-dock and under properties, in Installed Files, there's still a lot of files there. How can I delete it permanently?

Edit: duh I just delete the files from Synaptic :biggrin:

---

### Post by Watchtow3r on 2008-06-13
> **vapotrini said:**
> Yes, I do believe you're gonna have to uninstall the latest version for the one I posted to work. Think you're gonna have to remove it completely but I'm not 100%. 

The one I posted is the whole kiba-dock with physics, it's just an older verison. It doesn't have as many features as the latest kiba but IMO the physics just can't be beat. Besides, it's so much easier to install, simply download and double click to install... the end.

[http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb](http://stashbox.org/6310/kiba-dock_0.1-1.2_i386.deb)

OK I uninstalled the previous one, then downloaded and installed the one with the link you gave me, but all I get now is a little miniature dock with no icons in it. Here's a screenshot:

[http://img185.imageshack.us/my.php?image=screenshot2ws8.png](http://img185.imageshack.us/my.php?image=screenshot2ws8.png)

Also, the whole file you gave me is only 105.2 kb compressed. You said it's the whole dock in that file? How can it be so small?

---

### Post by crudolphy on 2008-06-14
Worked for me on Hardy Heron AMD64.  Followed procedure just as listed.  Only problem is a segfault that kills kiba-dock when power is cut to monitor after period of inactivity.  I don't use screensaver, just cut power to monitor.  If anyone else is experiencing this problem please post.

---

### Post by crudolphy on 2008-06-14
Update to the previous thread.  Has been running now for at least 12 hours, multiple times monitor had to "woken up" by mouse or keyboard activity without segfault.

This works really well.  I have deleted the panel at the bottom of the my desktop (that comes default with trashcan and workplace switcher) and replaced with kiba-dock.  I like it alot!:)

---

### Post by Watchtow3r on 2008-06-17
> **Watchtow3r said:**
> OK I uninstalled the previous one, then downloaded and installed the one with the link you gave me, but all I get now is a little miniature dock with no icons in it. Here's a screenshot:

[http://img185.imageshack.us/my.php?image=screenshot2ws8.png](http://img185.imageshack.us/my.php?image=screenshot2ws8.png)

Also, the whole file you gave me is only 105.2 kb compressed. You said it's the whole dock in that file? How can it be so small?

Any help?

---

### Post by mattgaunt on 2008-06-18
Watchtower i dont know if your going to get any help regarding using that file, but I've updated the how-to to include a bit at the end regarding getting the akamaru engine up and running. Go through the how-to again and then add the bit at the end of the how-to to get the akamaru engine working.

Gaunt

---

### Post by Sand &amp; Mercury on 2008-06-20
I'm having some trouble here... the first step, installing all the packages needed for compiling turns this up:

```
The following packages have unmet dependencies:
  libgtk2.0-dev: Depends: libcairo2-dev but it is not going to be installed
  libpango1.0-dev: Depends: libcairo2-dev (>= 1.2.6) but it is not going to be installed
  librsvg2-dev: Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
  python-gtk2-dev: Depends: python-dev but it is not going to be installed
                   Depends: python-gobject-dev (>= 2.14) but it is not going to be installed
E: Broken packages

```
Trying to install libcairo2-dev turns this up:
```
The following packages have unmet dependencies:
  libcairo2-dev: Depends: libcairo2 (= 1.6.0-0ubuntu1) but 1.6.0-0ubuntu2 is to be installed
E: Broken packages
```

---

### Post by mattgaunt on 2008-06-23
Have you enabled all repositories in synaptic? Im only guessing what the problem might be.

Gaunt

---

### Post by Eion on 2008-06-25
So, sorry for the noob question, but how does one go about adding a "shut down" button to Kiba-Dock?  I couldn't find it anywhere in objects and didn't find a place for kiba downloads online.

---

### Post by dakun on 2008-06-28
it sometimes says that i need the packages glib-2.0 and gobject-2.0 but those arent in the ubuntu repos.
for others i get the errors below

```

dakun@dakun-desktop:~/kiba-dock/kiba-dock$ ./autogen.sh

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.ac: not using Gettext
autoreconf: running: aclocal 
configure.ac:26: warning: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: configure.ac: tracing
autoreconf: configure.ac: not using Libtool
autoreconf: running: /usr/bin/autoconf
configure.ac:26: error: possibly undefined macro: AM_GLIB_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
autoreconf: /usr/bin/autoconf failed with exit status: 1

```

---

### Post by Jen5en on 2008-07-02
A quick yes/no question here, does the later versions of Kiba-Dock have physics? This is one of the things I find attractive, but I enjoy stacks as well... currently running an old physics version.

---

### Post by mattgaunt on 2008-07-03
as far as I know it doesnt have the akamaru physics engine in it no

Gaunt

---

### Post by chaosdesigner on 2008-07-08
when i try to start kiba-dock it tells me this:

** (kiba-dock:14007): WARNING **: Error (plugin-loader.c @ line 665):
	Failed to open Plugin Directory '/usr/local/lib/kiba-dock/global_plugins': Error opening directory '/usr/local/lib/kiba-dock/global_plugins': No such file or directory

	For a core dump, run kiba-dock with --g-fatal-warnings.


what should i do?

never mind i solved it

---

### Post by doxao0710 on 2008-07-13
i stuck in here
what should i do
:~/kiba-dock/akamaru$ ./autogen.sh --prefix=/usr --exec-prefix=/usr

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.in: 28: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: aclocal failed with exit status: 1

---

### Post by doxao0710 on 2008-07-16
> **doxao0710 said:**
> i stuck in here
what should i do
:~/kiba-dock/akamaru$ ./autogen.sh --prefix=/usr --exec-prefix=/usr

checking for intltool...
found intltool
checking for libtoolize...
found libtoolize
checking for automake...
found automake
checking for autoconf...
found autoconf
Running 'autoreconf -v --install'...
autoreconf: Entering directory `.'
autoreconf: configure.in: not using Gettext
autoreconf: running: aclocal  --output=aclocal.m4t
aclocal: configure.in: 28: macro `AM_GLIB_GNU_GETTEXT' not found in library
autoreconf: aclocal failed with exit status: 1

hello anyone?

---

### Post by mattgaunt on 2008-07-16
By the looks of it you need the gettext library, search synaptic for gettext, might come up under libgettext or something but not sure

Gaunt

---

### Post by navneetb1050 on 2008-07-21
Im a newbie at ubuntu. . 
I followed the rules and everything went well until i typed kiba-dock at the end. 

sha@sha-desktop:~/kiba-dock$  kiba-dock
bash: kiba-dock: command not found

Anyone?

---

### Post by talsemgeest on 2008-07-21
Means that kiba dock is not installed, are you sure you typed everything properly?

---

### Post by house of x on 2008-07-22
Well Im new to Ubuntu... Pretty much got tired of the same ol windows.. YAWN.. At the moment I am trying to learn both MAC and Linux for personal and professional reasons. This was a really good straight foward and very helpful tutorial.
I got no errors and everything works fine for me..
Thank you

---

