---
title: "Senior Project to create custom linux distro"
date: 2008-01-09
forum: Desktop Effects &amp; Customization
---

### Post by kdarkentity on 2008-01-09
Last night i had a great idea for my senior project which would greatly increase the performance and appeal of the average gnome desktop. My plan is to create a fairly stripped down, simple ubuntu live cd that allows you to choose from a series of custom themes and programs so that new users wont be immediately turned off to an unfamiliar environment.  

At my school there is already an entire lab of dual boot machines and another lab with 4 linux machines and soon the rest will also be dual boot. So there are already many students that are turned on to ubuntu and they aren't afraid to use it, however i hear them complain about not knowing where to find things and how to set-up and install things. 

My goal is to create a simpler and more familiar environment for the new users out there, "linux for noobs" if you will. 

The reason i am posting this mainly is because i know how to create custom themes and such, but i'm not sure where i should look to learn how to program linux applications and how to set-up a live cd that allows the user to decide what the os looks like when you boot it up. Also I am unsure how to allow the user to choose which applications are installed  during the installation process.

please share all opinions and ideas with me and any information that could aid me in learning how to do this.

Thanks In Advance!!

---

### Post by kb3hkg on 2008-01-09
I recommend you start [https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization") with the live cd. The rest is all very ambitious and I do wish you good luck with it.

As for the programming it really depends on what language and interfaces you plan to use. Are there any languages you already prefer?

---

### Post by kdarkentity on 2008-01-09
> **kb3hkg said:**
> I recommend you start [https://help.ubuntu.com/community/LiveCDCustomization]("https://help.ubuntu.com/community/LiveCDCustomization") with the live cd. The rest is all very ambitious and I do wish you good luck with it.

As for the programming it really depends on what language and interfaces you plan to use. Are there any languages you already prefer?

well i start programming in a couple of weeks and we will be programming with c++  which i have used from writing programs in robot C, but i've never made a stand alone executable program yet.

---

### Post by Dngrsone on 2008-01-09
Hate to tell you this, kiddo, but Ubuntu is pretty much "Linux for N00bs."

I'd go a little less ambitious and maybe build a live disc with a school-related theme (use your school colors and maybe the mascot in the wallpaper and logon icons and etc).

---

### Post by kdarkentity on 2008-01-09
> **Dngrsone said:**
> Hate to tell you this, kiddo, but Ubuntu is pretty much "Linux for N00bs."

I'd go a little less ambitious and maybe build a live disc with a school-related theme (use your school colors and maybe the mascot in the wallpaper and logon icons and etc).

Yes you are right about this , but i am going to make it even simpler then it already is by creating familiar themes such as a mac os x theme and a windows theme which will change and adapt the layout of the gnome menu. The problem is learning how to do it.

---

### Post by kdarkentity on 2008-01-09
I was reading about creating a custom live cd and it says that squash-fs tools does not work with ubuntu 7.10 yet but i can't help but wonder how then the makers of gos (Green Os) were able to make a custom live-cd of ubuntu 7.10.

---

### Post by kdarkentity on 2008-01-11
Is it possible to transform an already configured desktop into a live-cd?

---

### Post by kdarkentity on 2008-03-27
Well i have kind of modified what i originally intended to accomplish but i have finally made my first distro that i have named K-OS VE, i am not yet sure whether i will be releasing K-OS to the public as i need to check on a few things such as "copy-wright" infringement since i am using a Vista inspired theme that i acquired mainly from gnome-look i am not sure if i can actually release K-OS, But basically K-OS is still designed and will be supported with the idea of a "simpler" gnome environment with free tech support by me. 

 Right out of the box it can perform all of the effects offered by the grace of compiz fusion, the screenlets manager is available and is up and running by default with running screenlets, rythmbox and totem have been removed and have been replaced with VLC media player and skinned with the windows media player 11 skin to provide a nicer interface and support for more file types and wine is installed and configured so users can still use some windows applications need they do so. 

I am realizing that as i want to add more useful applications i have to start removing other applications and packages that are pretty useful if not required by the system. I have already been asked to import Opera into K-OS VE but i as it stands the smallest iso image i've been able to fashion thus far is roughly 697.6 mb in size. I am shooting towards keeping this a Live-cd rather than a live-dvd so in order to make opera and other apps easily available i have been creating bundled installer files on the desktop in the form of Launcher files. 

I consider my K-OS to be a Beta as i have accomplished most of the goals i intended to from the start, however there is still so much more that i could do that i still want to. But first i need to focus on freeing up more space so that i may install more apps. Such as i need to find an all in one alternative to the cd-player/ripper/and burner apps that come as a bundle. 

I will continue on these posts at a later time.

---

### Post by thiemster on 2008-03-27
You should also have an option to pick either gnome, kde, or xfce (and possibly more) desktop environments during the installation process. I know you want to keep it a live-cd, so maybe there's some way to download the desktop environment from the internet (which would also save space on the cd)

---

### Post by kdarkentity on 2008-03-27
> **thiemster said:**
> You should also have an option to pick either gnome, kde, or xfce (and possibly more) desktop environments during the installation process. I know you want to keep it a live-cd, so maybe there's some way to download the desktop environment from the internet (which would also save space on the cd)

Yes i agree, which is why after i have K-OS VE (Vista edition) i was planning on making other custom distros that use the other Desktop Environments. Actually Maybe i should call this version of K-OS with the codename K-OS GVE which would make it GNOME Vista Edition. And then Maybe I'll make K-OS KVE with the Knoppix Desktop Environment with a Vistaish theme or some other custom theme. 

Thanks for the idea's. Please feel free to post more.

---

### Post by thiemster on 2008-03-27
What I'm trying to say is you should only have a default set of programs and an installer on the live cd. When a user runs the installer, the desktop environment could be installed from apt-get (use of packages ubuntu-desktop, kubuntu-desktop, and xubuntu-desktop.) Then, once the user has installed the desktop environment, your theme (from the live cd) would be applied.

This way you would only need one live cd for all desktop environments.

---

### Post by kdarkentity on 2008-03-27
> **thiemster said:**
> What I'm trying to say is you should only have a default set of programs and an installer on the live cd. When a user runs the installer, the desktop environment could be installed from apt-get (use of packages ubuntu-desktop, kubuntu-desktop, and xubuntu-desktop.) Then, once the user has installed the desktop environment, your theme (from the live cd) would be applied.

This way you would only need one live cd for all desktop environments.

I see what you mean but i am trying to make it easier for new users, basically meaning i don't want to have to make a new user who knows nothing about linux or the environments have to choose an environment during a live session . I'd rather make separate distros and provide videos and screenshots on a website so that a user may choose which distro to try from there.

---

### Post by thiemster on 2008-03-27
Yea, I also see what you mean now. In the installer, though, you could put screenshots of the different environments, along with the (not very technical) pros and cons.

---

### Post by kdarkentity on 2008-03-27
> **thiemster said:**
> Yea, I also see what you mean now. In the installer, though, you could put screenshots of the different environments, along with the (not very technical) pros and cons.

Alright i see, i will consider your ideas. Thanks.

---

### Post by kdarkentity on 2008-03-27
> **thiemster said:**
> Yea, I also see what you mean now. In the installer, though, you could put screenshots of the different environments, along with the (not very technical) pros and cons.

Actually for another idea i could make a live-dvd that actually does have all of the different sessions installed and configured with different settings and themes and then the user can choose which one(s) he or she wishes to install.

---

### Post by thiemster on 2008-03-27
> **kdarkentity said:**
> Actually for another idea i could make a live-dvd that actually does have all of the different sessions installed and configured with different settings and themes and then the user can choose which one(s) he or she wishes to install.

Or you could include a live dvd like you said that contains all three desktop environments **and** a live cd that downloads the environments from the internet. That way you could have an internet installation cd for most users and an offline dvd for people who either have a weak internet connection or no internet connection.

---

### Post by thiemster on 2008-03-27
Whatever you end up doing, could you send me an email with a link to your finished project? My email is sccrules94 (at) gmail (dot) com

---

### Post by kdarkentity on 2008-03-28
I am thinking on removing the sound recorder, sound juicer and serpentine and so far i only know that i am replacing sound recorder with audacity, I want to have an all in one cd ripper and burner i just haven't ever used one for ubuntu yet. What would be the best choice for my K-OS Users as an alternative?

---

### Post by thiemster on 2008-05-01
whatever happened to the project? have you finished? if so, I'd like a copy of it.

---

### Post by kdarkentity on 2008-05-04
Its been put on hold for now, if you wish i can put up a copy of the beta 2 iso when i get the chance.

---

### Post by thiemster on 2008-05-14
> **kdarkentity said:**
> Its been put on hold for now, if you wish i can put up a copy of the beta 2 iso when i get the chance.

yeah, please do. I'd like to try it

---

### Post by kdarkentity on 2008-05-28
For any who were following this thread i wanted to let everyone know that i have reopened the K-OS project and i am currently building the 8.04 versions of K-OS such as K-OS tiny and K-OS GVE.

If anyone is interested i will post the 7.10 K-OS Beta 2 still.

---

### Post by kdarkentity on 2008-06-02
Now i keep having this problem ... 

"There was a problem creating the /home/remastersys/remastersys/custom.iso file. Please check the size of /home/remastersys/remastersys/ISOTMP/casper/filesystem.squashfs to make sure it is less than 4.6G.  If it is larger then you will have to either exclude more or cleanup the system further before trying again."

This is the output error i keep getting after trying to create an .iso image file with remastersys. I also keep getting an error that says something about my xauthentication could not be written 

What are possible causes of this. I am pretty sure i have sufficient space in my home folder for the .iso as well.

---

### Post by kdarkentity on 2008-06-02
The only other thing i can think of is that i upgraded the version of remastersys that i was using. I wonder if thats part of the problem.

---

### Post by thiemster on 2008-06-06
Sorry, but I'm not really sure why remastersys isn't working, as I have never used it before.

Could you send me a link to download a .iso file (torrent, or however else you're going to distribute them) to my email sccrules94 (at) gmail (dot) com

---

### Post by kdarkentity on 2008-06-06
I am almost ready to release the current version that i am working on as a K-OS 8.04 beta 1 actually.

---

### Post by thiemster on 2008-06-13
just email me a link to it when you release the beta

sccrules94 (at) gmail (dot) com

---

### Post by kdarkentity on 2008-06-13
will do, i would release the beta now but i am trying to figure out why i can't use custom icon themes or emerald themes with compiz at the moment.

---

### Post by NEUR0M4NCER on 2008-06-15
Hi - sounds like you're doing some great work. Just stumbled upon this thread, and although it's a little late, i'd like to chuck in my two cents - see what you think.

IMHO, One of the biggest put-offs about Linux - even Ubuntu (for n00bs as someone put it above) - is the sheer amount of choice. Bear with me on this, because I know choice *should* be good...

Let's use Ubuntu as an example: When a new user starts looking around the forums, and is thinking about d/l an iso, they're immediately hit with a choice - U*, K* or X*... or even Edu*. That's flustering at best, off-putting at worst. So they have a look into the differences, and (although it's true) the best answer they can find is "...well it all depends on what you want". Nothing very clear there.

So let's assume that they plump for Ubuntu, as it's recommended for new users. Once installed ("Oooh - Don't I need to install drivers or something?" :D), they have a look at some of the other apps available. 20 browsers, 20 window managers, office apps? Wow. Lots. You get the idea.

Now I reckon that for a school project (and poss a new distro) this should all be simplified, as was your intention from the beginning. Kubuntu had the right idea, but the K* prefix is just as confusing. I think you need to be very bold, and choose **one** desktop environment, **one GOOD** main theme (Windows managed just fine for years with one theme), **one** Office suite - etc. Then, re-jig the main menu, re-naming apps with definitions, rather than the app name: Image Editor; Web Browser; Movie & Audio Player.

Other 'useful' tweaks might be things like only using one desktop & removing the pager, not going 'all-out' with Compiz, 'cause whenever I show it to my friends, they assume I had to learn how to code in binary or something (even though I did it all through someone else's scripts), and are just scared by the complexity of it all: "so I move my mouse to this edge, this happens - alt&scroll makes things transparent - alt&tab is window switcher - ctrl&alt&f1 thru f6 is... BRAIN OVERLOAD!".

Don't get me wrong - if you were to release the above ideas as a distro, there would be a great many negative comments, somewhat akin to what people say about Gnome ("It's TOO simplified"), but for a project with the goal of simplicity & ease of use, these things NEED to be done. As it's based on Ubuntu, all of the settings are STILL THERE, just hidden under a nice, easy interface - perhaps even have an "enable advanced use" button in the menu, that shows all of the more complex things - Synaptic, Terminal, Compiz-Config, Gconf-Editor.

As I said, some bold choices need to be made, but when aiming a product at a specific demographic (i.e. non-technologically-minded folk), you can't please everyone - better to stick to your guns and do the best job you can for your intended audience.

Looking forward to seeing your finished work - be sure to post back when it's ready!

---

### Post by kdarkentity on 2008-06-15
> **NEUR0M4NCER said:**
> Hi - sounds like you're doing some great work. Just stumbled upon this thread, and although it's a little late, i'd like to chuck in my two cents - see what you think.

IMHO, One of the biggest put-offs about Linux - even Ubuntu (for n00bs as someone put it above) - is the sheer amount of choice. Bear with me on this, because I know choice *should* be good...

Let's use Ubuntu as an example: When a new user starts looking around the forums, and is thinking about d/l an iso, they're immediately hit with a choice - U*, K* or X*... or even Edu*. That's flustering at best, off-putting at worst. So they have a look into the differences, and (although it's true) the best answer they can find is "...well it all depends on what you want". Nothing very clear there.

So let's assume that they plump for Ubuntu, as it's recommended for new users. Once installed ("Oooh - Don't I need to install drivers or something?" :D), they have a look at some of the other apps available. 20 browsers, 20 window managers, office apps? Wow. Lots. You get the idea.

Now I reckon that for a school project (and poss a new distro) this should all be simplified, as was your intention from the beginning. Kubuntu had the right idea, but the K* prefix is just as confusing. I think you need to be very bold, and choose **one** desktop environment, **one GOOD** main theme (Windows managed just fine for years with one theme), **one** Office suite - etc. Then, re-jig the main menu, re-naming apps with definitions, rather than the app name: Image Editor; Web Browser; Movie & Audio Player.

Other 'useful' tweaks might be things like only using one desktop & removing the pager, not going 'all-out' with Compiz, 'cause whenever I show it to my friends, they assume I had to learn how to code in binary or something (even though I did it all through someone else's scripts), and are just scared by the complexity of it all: "so I move my mouse to this edge, this happens - alt&scroll makes things transparent - alt&tab is window switcher - ctrl&alt&f1 thru f6 is... BRAIN OVERLOAD!".

Don't get me wrong - if you were to release the above ideas as a distro, there would be a great many negative comments, somewhat akin to what people say about Gnome ("It's TOO simplified"), but for a project with the goal of simplicity & ease of use, these things NEED to be done. As it's based on Ubuntu, all of the settings are STILL THERE, just hidden under a nice, easy interface - perhaps even have an "enable advanced use" button in the menu, that shows all of the more complex things - Synaptic, Terminal, Compiz-Config, Gconf-Editor.

As I said, some bold choices need to be made, but when aiming a product at a specific demographic (i.e. non-technologically-minded folk), you can't please everyone - better to stick to your guns and do the best job you can for your intended audience.

Looking forward to seeing your finished work - be sure to post back when it's ready!

Thank you very much for your thoughts and opinions, everything you described is exactly what i am aiming for, i hope to create the most user friendly linux distro so far, without complicating things and by creating a nice clean common user interface much much like what users are used to seeing.

---

### Post by thiemster on 2008-07-12
have you gotten any farther along with the distro yet? If you've released the beta, please post a link to download it. I am a willing beta-tester.

---

### Post by kdarkentity on 2008-07-15
I actually have kinda let my personal life prolong its development so i haven't really been working on it for a while, i still need to get the emerald themes working.

---

