---
title: "installing Scilab/Octave or any other programmes.. HELP!!!!"
date: 2006-04-27
forum: Education &amp; Science
---

### Post by djbwhizz on 2006-04-27
Hi guys..

IM really new to ubuntu and linux.. so basically..im really having problem on installing my softwares and all.. i do realise that i would need to download it from the net.. but after downloading it.. i dunno wut to do...

currently..i need a program that is similar to matlab.. read that ppl suggested me to use octace or scilab.. downloaded scilab from the net.. but i still dunno how to install it.. nor to use it...

as for octave... i managed to install it using synaptics package manager... but still dunno how to run it nor to use it... 

same as well to other programmes that i might need in the future.. wut do i need to do to install it properly... 

i am faling in love wif linux.. but i guess i still haf lots to learn.. do help me out guys...

cheers.
kimie

---

### Post by Sutekh on 2006-04-27
[Octave](http://www.gnu.org/software/octave/) is very similar to MATLAB.  When I was at Uni, we used to use MATLAB in engineering, and Octave on UNIX machines in maths.  I found them to be quite similar.

To start Ocatve, simply open a Terminal or Run Dialog (Alt+F2) and use
```
octave
```
Arrays and matrices are entered exactly the same, and operations on them are the same.  Even functions follow the same format, and alot of commands are similar.

You should probably start with the [Octave Online Manual](http://www.gnu.org/software/octave/doc/interpreter/) for more help.

You might also want to install [GNUPlot](http://www.gnuplot.info/), which is also available in the universe repository (where you should have gotten Octave)

---

### Post by sl-gnome on 2007-05-08
I just downloaded scilab. I'm new to ubuntu too. I don't know how to install it.
Someone help me quick!

---

### Post by WW on 2007-05-08
> **sl-gnome said:**
> I just downloaded scilab. I'm new to ubuntu too. I don't know how to install it.
Someone help me quick!

When you say "I just downloaded scilab", do you mean you downloaded the file scilab-4.1-bin.linux-i686.tar.gz from the scilab web page?  Or did you get scilab-4.1-src.tar.gz (the source code)?

If you need the newest version of scilab (version 4.1), you'll have to get it from the scilab web page.  If you are OK with version 4.0, and you are running edgy or feisty, you can install it from the Ubuntu multiverse repository.  Assuming you have this repository enabled, you can use Synaptic to install the packages **scilab** and **scilab-doc**, or in a terminal you can run the command
```

$ sudo apt-get install scilab scilab-doc

```

---

### Post by ahmatti on 2007-05-09
I suggest that you also install gnuplot to get plotting working in octave.

```
$sudo apt-get install gnuplot
```

---

### Post by Pocadotty on 2007-05-09
Alternatively you can go to Synaptic Package Manager (System->Administration->Synaptic Package Manager) and do a search for scilab, and then mark for installation.  The command line option works just as well, but I prefer using the GUI.

Generally speaking, using repositories are the key to easy and fun Linux use.  So if you want an application, first search in Add/Remove Applications, then check Synaptic (some programs that are in the repositories, like scilab, don't show up in Add/Remove but they do in Synaptic), and if you still cant find what you need then look around on the internet, and make sure you chose the Debian packages as Ubuntu is based on Debian.

Or you could compile from source, but that can be a big pain and take allot more Linux knowledge.

Stick with the repositories and your life will be easier.

---

### Post by sl-gnome on 2007-05-21
> **ahmatti said:**
> I suggest that you also install gnuplot to get plotting working in octave.

```
$sudo apt-get install gnuplot
```

Ok I did what you told me. Chucked scilab and stuck to octave. You see, I don't know what to do after installing it. Can't seem to open it. I know this sounds ludicrous and rudimentary. Please help.
I found the folder that Octave is in, but I just can't seem to get my hold on it.
I downloaded Octave from the web and installed it( I think).
Now what>?

---

### Post by sawjew on 2007-05-23
Octave doesn't have a graphical interface so there is no menu entry.  To start Octave open up a terminal window Applications>Accessories>Terminal then in the terminal window type ```
octave
```

You will then be in an octave session and can use all the standard commands which are almost identical to Matlab  commands.

If you really want a GUI for Octave you can install Octave workshop following the instructions here [http://ubuntuforums.org/showthread.php?t=150310&page=5#42]("http://ubuntuforums.org/showthread.php?t=150310&page=5#42") in the second post or you can try Qtoctave from here [http://qtoctave.wordpress.com/what-is-qtoctave/]("http://qtoctave.wordpress.com/what-is-qtoctave/")

You could also try koctave ```
sudo apt-get install koctave
``` if you are using KDE but I have found it to be very unstable on Gnome.  Koctave is a very good Matlab like frontend though.

Your other option is to install scilab ```
sudo apt-get install scilab scilab-doc
```which gives a good graphical maths program with pretty well all the features of Matlab.

EDIT: I see you already tried scilab so ignore that comment if you like

---

### Post by slimdog360 on 2007-05-23
to be honest I think the scilab from the repos is a bit dodgy, for me its had a couple of probs. The downloaded version from their site is better. To install either read the read me or follow this. Untar the package, cd to the bin directory in the scilab folder, type 'make', now its installed to that folder. To run it just type 'scilab' in that same bin directory. 

If you didn't understand that then either read the readme or install it from the repos.

---

### Post by lunamystry on 2007-07-13
I cant find ocatve in the synaptic manager. There is Kocatve and when i try to run it, it says there is some error and it closes. I have tried to install an ocatve that i had for windows using wine but it does not start when I click the desktop icon. I the wine menu there is only the uninstall icon. I tried downloading .tar files and i couldn't install them. When I type sudo apt-get install ocatve i get this. 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

then i tried the:

tar xfvz tarball_name

and still didnt work. am I maybe typing the file name wrong? because I write the name of the file as it appers on the desktop. 

i found octave in synaptic and I downloaded it, pressed alt+F2 and tried to run it, and nothing happens. It appears in the wine menu for some reason. 

This is what appers in the terminal when I try to rub koctave which i newly installed

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kOctaveui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
No lib found, check that kdebase is properly installed!
QObject::connect: Cannot connect (null)::destroyed() to KApplication::quit()

Can anybody help?


thank you for your valuable time

---

### Post by WebDrake on 2007-07-13
> **djbwhizz said:**
> Hi guys..

IM really new to ubuntu and linux.. so basically..im really having problem on installing my softwares and all.. i do realise that i would need to download it from the net.. but after downloading it.. i dunno wut to do...

currently..i need a program that is similar to matlab.. read that ppl suggested me to use octace or scilab.. downloaded scilab from the net.. but i still dunno how to install it.. nor to use it...

as for octave... i managed to install it using synaptics package manager... but still dunno how to run it nor to use it... 

same as well to other programmes that i might need in the future.. wut do i need to do to install it properly... 

i am faling in love wif linux.. but i guess i still haf lots to learn.. do help me out guys...

cheers.
kimie

Octave runs from the command line---just type the command ```
octave
``` and away you go.  It'll put you in an "octave shell" (think of the command prompt in MATLAB).  N.B. You need to install gnuplot as well in order to be able to make figures.

You could also try installing KOctave (again via synaptics) which will give you a graphical user interface for Octave closer to what you get with MATLAB.  There's also octave-forge which contains a lot of contributed functions by Octave users.

If you're feeling adventurous there are also some Python libraries which enable you to replicate a lot of MATLAB functionality---have a search around this forum for MATLAB, I'm sure they've been mentioned many times before.

***EDIT:** Whoops, posted this without reading everything everyone else had written.  Not enough coffee this morning.*

---

### Post by WebDrake on 2007-07-13
> **lunamystry said:**
> I cant find ocatve in the synaptic manager. There is Kocatve and when i try to run it, it says there is some error and it closes. I have tried to install an ocatve that i had for windows using wine but it does not start when I click the desktop icon. I the wine menu there is only the uninstall icon. I tried downloading .tar files and i couldn't install them. When I type sudo apt-get install ocatve i get this. 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

then i tried the:

tar xfvz tarball_name

and still didnt work. am I maybe typing the file name wrong? because I write the name of the file as it appers on the desktop. 

i found octave in synaptic and I downloaded it, pressed alt+F2 and tried to run it, and nothing happens. It appears in the wine menu for some reason. 

thank you for your valuable time

I'm not sure why KOctave would have the error you describe but let's get Octave itself working first.  Let's begin by uninstalling your Windows/Wine version of Octave and sticking to the version in the Ubuntu repositories.  I would suggest---for now---that you forget about trying to install anything from source.  Get yourself comfortable with the package management system and how it works first.  We should be able to solve your problem like this.

When you typed sudo apt-get install octave, was Synaptics open?  Or were you installing updates?  If so, that's why.  Make sure that Synaptics is closed and try again, then it should work.

Last, Octave is what we refer to as a *terminal application*.  If you use the alt+F2 option, make sure to tick the box saying, "Run in terminal".  Alternatively, open up a terminal window yourself as others described above and type 
```
octave
```
at the command prompt.

---

### Post by akshayas1986 on 2007-09-11
Just for people trying to install Koctave on GNOME. As it appears, Koctave is for KDE environment and needs KDEbase. So bfore installing Koctave, execute this command
> sudo apt-get install kdebase

---

### Post by LaserJock on 2007-09-25
> **akshayas1986 said:**
> Just for people trying to install Koctave on GNOME. As it appears, Koctave is for KDE environment and needs KDEbase. So bfore installing Koctave, execute this command

Is kdebase not installed when you install Koctave? If not we should fix that.

-LaserJock

---

### Post by slimdog360 on 2007-09-28
> **lunamystry said:**
> I cant find ocatve in the synaptic manager. There is Kocatve and when i try to run it, it says there is some error and it closes. I have tried to install an ocatve that i had for windows using wine but it does not start when I click the desktop icon. I the wine menu there is only the uninstall icon. I tried downloading .tar files and i couldn't install them. When I type sudo apt-get install ocatve i get this. 

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

then i tried the:

tar xfvz tarball_name

and still didnt work. am I maybe typing the file name wrong? because I write the name of the file as it appers on the desktop. 

i found octave in synaptic and I downloaded it, pressed alt+F2 and tried to run it, and nothing happens. It appears in the wine menu for some reason. 

This is what appers in the terminal when I try to rub koctave which i newly installed

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file kOctaveui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
kOctave: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file editorui.rc
No lib found, check that kdebase is properly installed!
QObject::connect: Cannot connect (null)::destroyed() to KApplication::quit()

Can anybody help?


thank you for your valuable time

koctave is a frontend to octave, by that I mean you need octave to run koctave. The reason you cant install octave is you first need to enable the extra repositories. [http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources") you can use this as a guide.

Then once you do that you can install octave. My suggestion is putting this command into a terminal
```
sudo apt-get install octave octave-forge gnuplot
```

---

### Post by akshayas1986 on 2007-09-30
@LaserJock

Well I had to install KDEBase after installing Koctave. It was not working till I installed KDEBase. I guess Koctave does not install KDEBase.

---

### Post by pathematica on 2007-10-04
I read this thread with excitement but did not find an answer to a particular problem and I would be grateful for help which might also assist in a deeper understanding of how unix like OSs in general and ubuntu in particular works (I have been using SuSE and found ways to struggle through but it seems it has not left me with insight into certain basic concepts).

Anyway, I have successfully installed scilab using synaptic.

Like the original poster, it was not obvious to me how to launch it. 

I could not find a way to open a terminal - that is obviously a very bad thing in itself for someone trying to use any 'nix system! Eventually I found that my applications menu was missing the accessories folder, and that has been corrected. Just in case that was the problem (don't really believe it was!) I have mentioned it here.

With the terminal found and opened, typing scilab launches the program. An error message is given in the terminal but scilab opens anyway (mentioned here as it might be important in another problem to be discussed later). The error message (or rather the message given in the terminal before scilab opens) is

/usr/bin/scilab: 28: /usr/lib/pvm3//lib/pvmgetarch: not found

As I have said, scilab opens anyway. 

I presume from this response that the binary (forgive me if I do not use the words correctly) is located in the folder "/usr/bin/" and I presume it is called "scilab". My understanding gets a bit hazy here but I think this invokes something called a shell script which I presume is similar to a batch file in the ancient msdos. I presume therefore that the script opens whatever files are required and presumably adds what I would have once called command line parameters. I presume the apparent error message is a warning that some configuration file or something is missing. I do not really know.

Anyway, I tried to add an item to the launch menu accessed from "applications" on the top left of the screen (it is a convenience thing - please indulge me that I would want to do this!). Right clicking "applications" allows me to choose edit menu from which I can select "add item" from a panel. This allows me to give the menu item a name (I called it "Scilab" as I have no imagination". There is a panel to enter the launch command, with a button called "browse" which is clearly the best way to go about populating it with the correct address of the program. Navigating via filesystem through "usr" and "bin" allows me to find what I understand to be a shell script called "scilab" - this all looked pretty good and I was feeling smug at this stage. I set the "Type" to "application in terminal" to avoid that pitfall and I was on smugness overload by then. I clicked the various ok and close buttons to cock the gun and prepared to pull the trigger by selecting the new item "Scilab" which was there in all of its glory from the applications menu. 

However, the unix gods saw my arrogance and punished me by a window that opened and closed in a flash with nothing else to show for it. I can only think that I am stupid or that other error message in the terminal is important. 

Also, I would be grateful is some kind person would explain where the key files that launch programs are placed (or point me at a forum where such things are discussed) - it seems there is no consistency in the use of /usr/bin/ or /usr/lib/ or a bunch of other alternatives that I have seen. I presume this is no more problematic than launching executable programs directly or from batch files as long as the command is issued from the correct directory or the directory is specified or it is mentioned in something comparable to a "path" statement in dos. 

Any help on speedy launching of scilab or deep insights into ubuntu (and other 'nix systems) gratefully accepted!

---

### Post by pathematica on 2007-10-05
Ironically, less than one day after the previous post, openSuSE 10.3 has been released and, on reading through their introduction, I found this page:

[http://www.novell.com/documentation/opensuse103/opensuse103_startup/index.html?page=/documentation/opensuse103/opensuse103_startup/data/book_opensuse_startup.html]("http://www.novell.com/documentation/opensuse103/opensuse103_startup/index.html?page=/documentation/opensuse103/opensuse103_startup/data/book_opensuse_startup.html")

It includes a brief description of the intended content of the various folders whose names newbies like me find exotic, opaque and sometimes not what what appears to be the best guess (for example, as I imagine many of you experienced hackers will know, "/usr" refers to "UNIX system resources" not the more appealing (for a newbie) "user".

I presume there may be a similar introduction to the gnu/linux system in ubuntu forums and I will search for it (any short cuts to this search gratefully accepted).

I would still be grateful for any advice/explanation relating to my failure to start scilab from a menu shortcut - the extra information from suse has not helped me there!

Best wishes

---

### Post by pathematica on 2007-10-05
Sorry if I seem to be talking to myself but on a whim I tried something else that adds to the understanding/mystery.

I had not mentioned it before but I have already installed the stats program R, which also runs in a terminal. I had successfully added a menu item to the applications launcher, with the option selected of opening it in a terminal. For the command, I had put "/usr/lib/R/bin/R" (chosen after searching for files that might be the binary that launches the program). This worked fine, adding to the mystery of why I could not get scilab to launch, the only apparent difference being the error message that appears when launching scilab (there was none when launching R in a window).

Anyway, it occurred to me to substitute simply "R" for "/usr/lib/R/bin/R" - as you experienced types will predict, R still opens from the applications menu so it would seem a detailed directory path was not needed (reflecting the situation when running the program from the command line in a terminal window).

So, excitedly, I substituted the simple "scilab" in place of the attempted guess at the detailed command including the path and ... it still does not work.

So, I would still be grateful for any comments/explanations.

---

### Post by r4e on 2008-04-15
> **pathematica said:**
> 

With the terminal found and opened, typing scilab launches the program. An error message is given in the terminal but scilab opens anyway (mentioned here as it might be important in another problem to be discussed later). The error message (or rather the message given in the terminal before scilab opens) is

/usr/bin/scilab: 28: /usr/lib/pvm3//lib/pvmgetarch: not found

As I have said, scilab opens anyway. 



Hi there, pathematica,

This may be a bit late for you, but for anyone else having similiar problems to get rid of the, "pvmgetarch: not found error," install the pvm package:

Type the command:

```

sudo apt-get install pvm

```

To take care of this for future users, pvm should really be made a dependency of scilab by the package maintainer.

Secondly, you can either launch the scilab GUI from command line or you can run it headless:

With GUI:

```

/usr/bin/scilab

```

Without GUI:

```

/usr/bin/scilab -nw

```

Hope this helps...

r4e

---

