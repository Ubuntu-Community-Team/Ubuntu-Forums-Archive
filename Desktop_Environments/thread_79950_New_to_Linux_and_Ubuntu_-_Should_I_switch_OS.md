---
title: "New to Linux and Ubuntu - Should I switch OS?"
date: 2005-10-21
forum: Desktop Environments
---

### Post by Ingla on 2005-10-21
Hello. 

I've been wanting to migrate to Linux for a long time...if I can get readonably good functionality. That is the key. I need the computer for business, etc...not just a hobby. 

I'm having various problems with Ubuntu. Some of which are critical to my operations...some less so. I'm hoping those who have come before me can give me some advice...either how to get Ubuntu working well, or even tell me I'd be better off with KDE or something. Here goes>

1. Multilanguage support:
I need to work in several languages. One is Hebrew, which seems especially problematic as it is written from right to left. Even Microsoft has issues with this, but at least it works.

I installed language packs and support for these languages, but can find no way to switch languages (keyboards). I saw a post somewhere which said it couldn't be done in Ubuntu and the guy had switched to Susse. Another said he managed to get it to work, but only by having different users...each with a different locale and default language (presumably, that means the whole interface has to be in another language). I could possibly function somehow in such an environment, but it would be EXTREMELY inconvenient to conduct normal business that way.

Open Office can't seem to do languages, so I installed Avi. which is supposed to be able to write 30 languages, including Hebrew and Arabic. Not that I can see. It just writes English. A similar program for Windows (Accent) has a drop down window to choose your language and self-contained fonts). I see no way to change languages in either of these Linux programs. Maybe the problem is Ubuntu...maybe not. 

I don't see any installed fonts for the language packs I've put in (looking from Writer, Avi and the Fonts Folder). What's installed and how do you get it to work?

Even if there are commands to switch languages, using command line in the middle of writing multilingual documents just won't cut it. 

I have a friend who runs some KDE distro, who has a Hebrew keyboard working. Maybe Ubuntu isn't for me and I should start again in Kubuntu (before I get this drive set up too much)...if KDE can do it.

Any experience with this? Ideas?

2. Antivirus:
Although there are those who claim Linux can live without an antivirus, I doubt that will continue to be the case. As Linux gains ground in the world, the virus writers will surely not be able to avoid the temptation of new and largely helpless victims.

I have installe ClamAV, and ran a scan. BUT a command line antivirus is virtually worthless. The first thing a "good" virus does is knock out the antivirus program. You have to have real time protection with e-mail scanning, automatic detection of viruses in downloads, etc...just like every Windows antivirus provides.

There's supposed to be a GUI for Clam which can do this, but I have not been able to get it up and running.I saw somewhere that it has some dependency that requires me to deal with the kernel. Oh oh.

In Synaptic, I installed an antivirus called Aegis. It said it put it in Apps>Accessories...but it didn't...or anywhere else I can find (unistalled and tried again but no go).

3. General Problem with Installations:
Anything not installed by Synaptic (and sometimes apt) has no link, usually no instructions as to what command runs it. In short, it's on the drive but totally useless. On several occasions, I've had to e-mail to vendor to find out how to open the program. Is this just a general Linux problem?

It's especially severe with the tar.gz. downloads. Usually, there's just no way to know what file to run or what command to run it with. Anyone have any advice on this?

4. Online streaming radio.
Can't use it. I'm running Firefox and the player is Totem. Totem is called automatically but can't run anything. I get an error message saying Totem can't find a Gstream object...check Gstream. How in the world am I supposed to do that? I've installed everything in Synaptic with the word gstream in it. Nothing!

I installed Xine (with GUI). Comes up but can't connect to anything on it's Media List. I get a message that it needs a plugin. A plugin? For its own basic function on its own internal list? Wow! Where would I find such a thing.

5. Strange Problems:
a. I can't set the time. It asks for a root password..I give it and get in...set the time and then get a message saying that root login failed a Child xxx. However, sometimes the time was, in fact, set and sometimes not. Anyway it reverts back to the wrong time even though the correct time zone is configured.

b. Some programs run and then immediately hang. They can be minimized but not closed. Then, when I maximize them again, the GUI is blank...just a framework. By the way, I'm running 512 RAM and a 2.4 CPU, so this shouldn't be a memory problem...even though it looks like one. I have to restart Gnome to get rid of it, but if I run it again the same thing happens.

c. Installed all updates including new themes, but can't use them. If I try, it says "install" but doesn't say where (Ubuntu doesn't know where it keeps its themes?!). Everyplace I try brings me "invalid location to install".

d. In Terminal, I often can't work with files that are not on the Desktop. No matter what path I type, I get "file not found". If I move it to the Desktop, I can do what I want with it.

6. Need Good Programs:
This is apparently a general Linux issue. Programs just aren't as user friendly. OK. But I need functionality.

a. HTML editor. I use 1stpage. I know I won't find that in Linux, but isn't there an editor which will let use see the results while you working?

b. Antivirus. As mentioned, something with GUI and real time function (that doesn't cost hundreds of dollars).

c. E-mail. I use Incredimail (I know, I know) for two reasons. 

It allows me to create and use various kinds of business stationery. In Windows, I could work around this because I have a Mail Server and Mailing List Manager. In the list manager, I can type a plain text message and then attach an HTML file (containing the same). It will then send a multipart message. Thus, I could conceivably create e-mail stationery templates and use them to make messages. A real pain compared to Incredimail, but possible. Problem is I haven't found any programs like that for Linux. Any suggestions?

Second reason: Irun some web sites, so I get spam and viruses on some accounts. Incredimail has the ability to let me see messages on the server and delete without ever downloading to my machine. There aren't many programs that do that...even for Windows. I heard of one that could do that on Linux, but can't find it. Anybody know?

d. Images. I need to make images for the Web, including animated gif's and image maps. Can any Linux programs handle that in a user friendly way?

e. FTP client for managing my sites.

I know this is long and covers a lot of issues but, if anybody can address one or more of them, it would be a big help. Especially, before a put in too much work, would I be better off with KDE?


Many thanks to anyone who can help with any of this.

---

### Post by bete on 2005-10-21
I am wondering about NR.3 aswell....

Anyways:

NR.4 : Check out this link [http://ubuntuforums.org/showthread.php?t=79868&highlight=videos+firefox]("http://ubuntuforums.org/showthread.php?t=79868&highlight=videos+firefox")

---

### Post by Ampersand on 2005-10-21
1) I tend to use UIM for Japanese input support, not sure how well it works with other languages. I've seen discussion of Hebuntu, a Hebrew version of ubuntu. Not sure how far this has got.

3)Generally, installed programs can be run by typing their name in a terminal. If you type the first few letters of the program name (for example 'aeg') then press Tab twice, you'll be given a list of programs starting with it.

5)
a) You should be using the same password that you use to log in here most of the time.

6)
e)gftp works for me

---

### Post by phil_n on 2005-10-21
[QUOTE=Ingla]
3. General Problem with Installations:
Anything not installed by Synaptic (and sometimes apt) has no link, usually no instructions as to what command runs it. In short, it's on the drive but totally useless. On several occasions, I've had to e-mail to vendor to find out how to open the program. Is this just a general Linux problem?

It's especially severe with the tar.gz. downloads. Usually, there's just no way to know what file to run or what command to run it with. Anyone have any advice on this?
[/QUOTE]

I have this problem quite often with Linux. I put it down to lack of experience - it would be more obvious where stuff got installed if I understood the layout of the directory tree, and that will come with more reading and messing about, I guess. It's usually possible to install stuff in your home directory, which makes it easier to figure out.

Normal procedure for a tar.gz download for me is to unzip the contents into my home directory using the graphical tool that comes with Gnome, then go have a look at what's in there. If you've downloaded a binary then it should be relatively obvious by the name. For source code, installation almost always follows the pattern:

```
./configure
```
check output to see if I need to install any more packages, and apt-get as appropriate, then rerun configure if it failed the first time
```
sudo make && sudo make install
```

Alternatively the website you got it from will often have a Getting Started section that explains how to get up and running.

[QUOTE=Ingla]
b. Some programs run and then immediately hang. They can be minimized but not closed. Then, when I maximize them again, the GUI is blank...just a framework. By the way, I'm running 512 RAM and a 2.4 CPU, so this shouldn't be a memory problem...even though it looks like one. I have to restart Gnome to get rid of it, but if I run it again the same thing happens.
[/QUOTE]

Do you know how to add something to the panel (the strip across the top of the screen)? Right click it, hit Add to Panel, then have a look for a button thingy that kills an application. Then you can click the button on the panel, and click the empty window, and it will kill the process that's running the window. This isn't always 100% successful though - for example, aMSN has 2 processes running and if it crashes I've had to use ps -A to find the other one (which doesn't have an obvious name, but you can spot it by invoking aMSN again and keeping a watch on the process names) and then ```
kill
``` the process.

[QUOTE=Ingla]
d. In Terminal, I often can't work with files that are not on the Desktop. No matter what path I type, I get "file not found". If I move it to the Desktop, I can do what I want with it.
[/QUOTE]

I wonder if this one isn't connected to your problems with the root password. If you type ```
cd /etc
``` and then ```
ls
``` what happens?

---

### Post by GeneralZod on 2005-10-21
That's a fairly long list of deficiencies there and, while some of them are doubtless fixable, I'm not sure that Linux is ready to fully meet your needs.  If you were a home user wanting to try it out for a bit of fun, I'd probably say go for it, even so; but as your business may well be riding on it, I'd advise extreme caution.  In fact, I'd be tempted to offer up a verdict of "If it ain't broke, don't fix it" :)

---

### Post by Ingla on 2005-10-23
Hello.

I want to thank everyone for the replies. They have been very helpful - either directly or through suggested links, etc. 

To phil_n: When I type: cd /etc and then ls, I get a list of things...some highlighted. Is that the list of running processes? There are quite a few...all with pretty much non-descriptive names. Don't know what to kill. Or am I understanding you all wrong.

Some of the issues I mentioned in my first post have been solved or at least seem on the way to solution. Right now, I need to work on the multilingual problem, so I'm going to start a new post about enabling language support in the hope someone with Hebrew experience will pick up on the questions.

Thanks again.

---

