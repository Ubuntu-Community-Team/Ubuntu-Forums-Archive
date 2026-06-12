---
title: "Graphics for the future"
date: 2012-02-11
forum: Desktop Environments
---

### Post by UltimateCat on 2012-02-11
Hi
Since November of 2010 my graphics in Ubuntu 10.01/Ultimate Edition have hosed and or crashed twice now.  After painstaking trouble shooting and the help of Linuxquestions I have put my time and efforts in with the Senior Members at Linux to solve these graphics issues. 

I am wondering is there anyone out there in the Ubuntu community experiencing the same type of problems and would they be willing to work with me? ( so that this graphical interface issue/problem can be solved for future purposes.

In a way I'm asking a lot but this is extremely annoying and it may even be an aid/help to the Gaming and Leisure community.

The first time I lost all of my graphics it was due to " installed updates" and an "upgrade to the 2.6 version of the kernel.  
The second time my graphics crashed; a friend was playing Grand Theft Auto on my Windows side of my partition. ( I am seriously considering  the complete  removal Windows XP) 
The second time the graphics crashed I noticed that a file was either broken or corrupted.....still investigating that.

Anyway, Just want to get a feeling of what people think and feel about this.
If interested, intrigue, or otherwise....please give me your input.

---

### Post by bluexrider on 2012-02-11
You may want to give the readers a little more information. IE: Video Card, Memory you know some specs to go by.
Just a suggestion

---

### Post by UltimateCat on 2012-02-11
Thank you bluexrider
That's a good suggestion.

The graphics card involved is the ATI series-
Specifically the ATI/AMD Radeon 3100 Graphic PCI by ATI Technologies, Inc.
Driver version 8.54l.0.0

I have also went to:
[https://wiki.ubuntu.com/X/Troublesho...from%20scratch](https://wiki.ubuntu.com/X/Troublesho...from%20scratch)
and fully read everything and uninstalled like the documentation recommends. This was the cure for one time.  I'm interested in a cure for all time.

And in the past from graphic crashes it appears to have a fglrx installed but not configured to use it so I had to combined 2 xorg files together by use of sudo cp/etc/X11/xorg.conf-backup-xxxxxxxxxxxx/etc/X11/xorg.config.... for the Catalyst Control Center to start.

---

### Post by UltimateCat on 2012-02-14
Anyone know how I would test the RAM?

---

### Post by UltimateCat on 2012-02-21
Does anyone know if underclocking the graphics card a bit would help?
And if so;
How would I go about doing that?

---

### Post by UltimateCat on 2012-02-25
I am pretty certain that the graphics card I have is integrated circuitry that shares RAM and requires the motherboard and output for the chipset.

If it was the hardware failure then each time I turn on my system I am assuming that the graphics would fail after warming up so I don't think it's the hardware.

I found Memtest to test the RAM- I really don't think it is the RAM-

I started this thread about 3 weeks ago and hoping someone will elaborate-

What do you think?

Anyone?

---

### Post by UltimateCat on 2012-03-03
If anyone knows how to get into the BIO's for the graphic's card please post.

Not sure if those BIO's have a log but I am trying to find these 2 things out.

What's the difference between the BIO's for the OS and the BIO's for the Graphics card?

Some forms of communication between the motherboard and the processor is what I am wondering about.

So far I have found that it is eaiser to build and design graphics than to repair/reconfigure and execute commands for graphics that have been compromised/crashed in some way.
Getting into the logs may or may not be the answer-


Thoughts? Anyone?

---

### Post by 23dornot23d on 2012-03-04
The thing is ..... nearly everytime there is a problem with graphics - and this is just
my opinion as no doubt a lot will be running their systems just fine.

ATI and certain models just do not seem to play well ..... with Linux.

Its worth doing searches .... in [[COLOR=Blue]_**google on the card and solved.**_[/COLOR]]("https://www.google.com/search?q=Radeon+3100+Graphic+PCI+solved#hl=en&sclient=psy-ab&q=Radeon+3100+Graphic+PCI+solved+linux&pbx=1&oq=Radeon+3100+Graphic+PCI+solved+linux&aq=f&aqi=&aql=&gs_sm=3&gs_upl=11542l14739l0l14889l6l6l0l0l0l0l133l740l0.6l6l0&gs_l=serp.3...11542l14739l0l14889l6l6l0l0l0l0l133l740l0j6l6l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=abb779961339529e&biw=1144&bih=495")

From very early on all I have ever used is Nvidia ... the 9300 gsm is great for me -
but I run this in a laptop ....

The 6300 is a very old one and that is in my Desktop machine .... again no problems.

The latest is the 540 in my new laptop  .... and that one is a hybrid .... although I am not as happy with this as its new ..... given time I am sure something will get sorted.
(Ironside works for me ..... for Hybrid - switches between intel and nvidia to save power)

Thought I would reply as you seem to have had little response to a question that is
quite common ..... graphics and why they do not set up properly all the time.

Maybe if the drivers could stay static and kernels did not change we would be ok.

As time as gone on I think ATI have got better .... but I believe in the older times
there was less sharing of the workings of ATI graphics cards ....

> 
Find out what Graphics you are running

lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'


---

### Post by 23dornot23d on 2012-03-04
> 
If anyone knows how to get into the BIO's for the graphic's card please post.

Not sure if those BIO's have a log but I am trying to find these 2 things out.

What's the difference between the BIO's for the OS and the BIO's for the Graphics card?
My view on this as a 3D designer not a programmer ....  

* ( Laymans overview - simple and hopefully somewhere close to what goes on ) 
[URL="http://en.wikipedia.org/wiki/BIOS"]
[COLOR=Blue]_**BIOS ( initial settings )**_[/COLOR] [/URL]resides on a chip inside the computer ..... 
usually available by holding a key down at boot - allows boot order etc to be set up ......

The Basic Input Output System ( BIOS ) gives the computer as it says the Basics to allow it to talk / 
communicate with devices ......

Usually you will find settings in there that cover things like the [[COLOR=Blue]_Graphics adapter_[/COLOR]]("http://en.wikipedia.org/wiki/Video_card") ... the Printer ... the Hard Drives
The Modem etc ....

It gives the computer a initial state to start from ..... with some factory defaults .... and the user can 
override and change some of these to suit ...... one being onboard Graphics .... or AGP/PCI Graphics

as some motherboards have a slot for a new Graphics Card to be added ......


( After there seems to be a stage here where the Grub2 and the Kernel work together to find the Graphics Card ..... 
The Monitor and the resolution that it can run at .... plus other hardware settings - but seeing as we are just talking 
graphics here we will only explain that part of it  - which changes depending on if its a LCD or CRT  Monitor it will 
attempt to set things up correctly for them )

[COLOR=Blue]_**[The KERNEL]("http://en.wikipedia.org/wiki/Kernel_%28computing%29") **_[/COLOR]and [[COLOR=Blue]_**GRUB 2**_[/COLOR] ]("http://en.wikipedia.org/wiki/GNU_GRUB")......... ( secondary stage )

In here all the intricate details are picked up ...... and the computer hardware is set up and the program
to kick it into action ..... More details on the Graphics - specifics - plus Sound Card Modem Disks etc .....

[[COLOR=Blue]_xorg.conf_[/COLOR]]("http://en.wikipedia.org/wiki/Xorg.conf") sits in here and passes information out that can override some of the system settings for graphics 
 ... to allow the user to alter it correctly .... 
( every year the information in here - gets to be less and less - but as far as I know it is still one
way to get the correct information into the system - if the USER knows what they are doing )

[_Jockey_]("http://home.gna.org/jockey/") - seems to be a monitoring system that reports back if there are problems ..... with devices ... (debugging tool)

[_Plymouth_ ]("http://en.wikipedia.org/wiki/Plymouth_%28software%29").... is a intermediate stage that displays a logo ... or 4 dots flashing to let you know
that the system is working ..... also saves the user from seeing any errors should they be occurring
in the background - it also handles the display settings ..... and often this is where the user will
  find some problems .... but they are not always related to graphics .... we used to be able to press the <esc>
key here to see detailed information about what was working and what was not ..... this all seems to
be hidden now .... ( the way to get to it - is in the dir /var/logs )

( This seems to have been taken from the Windows Standard - which some versions of LINUX have now adopted ) 
[COLOR=Blue][U][B]
Login[/B][/U][/COLOR] ( Third Stage .... you only see this if the Autologin is not set ) for choosing the Desktop

Gnome Unity E17 KDE XFCE LXDE ..... etc

[COLOR=Blue]_**Desktop**_[/COLOR] ( fourth stage that the user sees )

This last part basically is laying out the screen in a nice format to use and giving links to useful programs 

here you can go to Additional Drivers ...... and choose different Graphics Drivers if your computer can
use them ......


Well thats as much as I know .... others may have a more detailed account of it ...... but this explanation
gets me by when I try to work out WTF is going on when I get a Black Screen and a White Flashing 
cursor ....... as that bit is the most annoying bit ,,,,, and hopefully not many USERs will ever see that. ;)

---

### Post by UltimateCat on 2012-03-07
23dornot23d:
   I appreciate you writing to me as it has been almost 3 months since I typed the thread and was starting to wonder should I just mark it Solved-

Anyway, the info. you gave was like GOLD to me.
It adds to the weeks of study I have done on my own.( Extremely nerverackin)

You said that there is a stage where Grub and the Kernel work together to find the graphics card....I am pretty sure it's when the interface in turn communicates with the software and than the software makes calls to the video/graphic BIO's-
Other than that all I know is that the chip to the BIO's contains instructions that speaks to the interface.
I got:
```
dir/var/logs

```
Thank You 

I hope to get into the graphics BIO's and maybe even underclock the card is the answer?....But I am determine to solve issues like broken graphics and black screen.....and the like-
 I'm an Oil painting Artist and if there is one thing I can't stand is a picture that doesn't look right-

You said; " A black screen and white flashing cursor "
Now that would really **** me off!.....I can relate to how you feel!
Hope that in the future it never happens again.
That fact that you took the time to help and write to me is worth more than I could use words to say:D
Thanks again!

---

### Post by 23dornot23d on 2012-03-07
> 
I'm an Oil painting Artist and if there is one thing I can't stand is a picture that doesn't look right-
This is a quote that I like ....

My Father was a perfectionist and a roofer ..... and the way he treats anything in life is to make sure that it gets put right to the best of his ability ..... and I do not mean that individually - if you need to ask someone to change something down the line to make things easier and better you do it ..... joiners can make a roofers job easy or hard.

( Water leaking into someones house is not acceptable - so things tend to get fixed properly ) 

I myself and me ....

A group of people with wide based talents can make a better job of anything - through
organization and helping one another ....

Out of all the industries on the planet ...... LINUX possibly has the biggest combined workforce ....... and potential.

The amazing thing that gets me - we work together as a team and no one is in charge - and no one appears to force anything on the people that are in it .... and there are no
set hours for this work ...

But if the people do not like something - then they work together to paint that OIL
painting together .... taking out any blemishes ..... but aiming towards making it look feel and work right for them - with the additional options for users to add their own personal touches ( customizing things ) to it - giving different variations on a theme.

If only we could make a proper LINUX based - Artificial Intelligent database here on the Web too ....
( Google is the closest thing to it for me - main keywords ..... Solved - Linux - Problem )

It would then really expand and improve at a much faster rate ..... just pulling out
the most useful pieces of information .... maybe like in code there could be a tagging
system ..... to grab things from the library .....

As with me - the time we spend searching for solutions could be reduced.

Back on topic .... 

I do not think changing the clock speed on a graphics card is the main issue but it
is possible - using Nvidia-Settings on Nvidia cards ......

But its more to do with how the system picks up things like resolution - monitors - and settings needed for specific graphics cards ..... one could be the graphics card clock
speed .... but I have never really looked into this on my Nouveau setup as the fan
never kicks in - and the graphics are dreadfully slow compared to how I used to
have it .... with the proprietary driver ..... 
( given up now - my system knows better - so nouveau is used  .... ) 

What monitoring tools are available .... ? 

[COLOR=Blue][B]I used to use Conky and pick the setting for the Nvidia Graphics Temp as that is quite important ...... and can vary quite a bit from computer to computer and desktop to desktop .... testing here showed me some things that I never realized
before taking part in it .... [COLOR=Black]

Nvidia-Settings[/COLOR]

Has some control over the speed it runs the the graphics ..... if proprietary drivers are used. 

I have not seen anything similar to this on Nouveau though .... maybe this
is where we need to search .... for changing the graphics performance modes.
[/B][/COLOR]
1 ..... The Graphics Card auto pick up  ....this is the number one problem to me .... 
USERs buy graphics cards to meet their needs .... and some are as expensive and more expensive than the full motherboard for price. 

* ( The need to use graphics to its best is one thing that can make a computer really appeal to the masses - as graphics in itself sells computers - advertisers would be lost without all the graphics and effects they use to sell things nowadays ) 
[COLOR=Red][B]
ATI and Nvidia[/B][/COLOR] still appear to be pushing the boundaries on a realistic 3D rendered world on a 2D screen.

2 ..... Next for me the system should find the best resolutions  available and display them .... 
( The user should then be able to choose and set the one that is good for them - in terms of speed and visual appeal - [COLOR=Red]**the user needs to have a choice here**[/COLOR] - balancing performance with what they need to use their computer for ..... )

3 .... The Monitors ..... Point to take into consideration here - the system again can make some odd choices .... 

I often use 2 monitors but rarely does the computer pick them both up from boot and use both of them properly ... ( [COLOR=Red]**one of them will switch off**[/COLOR] ) .... and often when getting to the desktop only one is recognized in the Settings Manager ..... and both monitors are set to one resolution only - which appears odd between a square CRT monitor and a LCD oblong monitor.

Things have got much better over the years though ( can remember back to a time when burning 12 install CDs to find only one would set my old [[COLOR=Blue]_**Sis graphics card**_[/COLOR]]("https://www.google.com/search?hl=en&gs_nf=1&tok=SbIUUyjhZBgnJLIQ17tpGg&pq=s1+graphics+card&cp=3&gs_id=10j&xhr=t&q=sis+graphics+card&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&biw=1148&bih=490&um=1&ie=UTF-8&tbm=isch&source=og&sa=N&tab=wi&ei=ATJYT7nWKeSn0QXw0fntDQ") up ..... 

Things can still be improved if there is an addition for advanced graphic card settings and a place the USER can input some basic overrides if they believe they are needed - at the moment xorg.conf is the only way I know how to change things .... and if this should be removed completely ..... does it then mean that they have bottomed the
graphics card problem ...... or does it just stop some people in their tracks for
upgrading .....  

( The other thing is that people can have their computers 5 years or more and know what the best driver - what resolution to use - and know what monitors they have ) 

Yet every six months things seem to change .... and the system re-evaluates ...
giving the USER some new headaches ...

[COLOR=Red]**So an option to take a snapshot of the 3 major parts of the GRAPHICS settings before a upgrade**[/COLOR] and to be able to re-use them ....  would be bliss ..... or a rolling release where the graphics only ever get changed if the USER gets a new graphics card then that is the only time they may need to change things ...
[COLOR=Blue][B]
If the USER gets a new computer then obviously a fresh install and brand new settings are then required  ..... not everyone is that lucky though.[/B][/COLOR]

War and Peace again .... graphics is something that means a lot to me. :)

---

### Post by grahammechanical on 2012-03-08
@UltimateCat

This is the comment that stopped me replying

> I am wondering is there anyone out there in the Ubuntu community experiencing the same type of problems and would they be willing to work with me? ( so that this graphical interface issue/problem can be solved for future purposes.

There is nothing wrong with this comment. I thought that you were inviting people to cooperate on a personal project. I did not think that you were inviting a discussion right here on this thread.

I do not have any answers or suggestions to give and that is another reason why I have not responded.

There is this link.

[http://ubuntuforums.org/showthread.php?t=1743535]("http://ubuntuforums.org/showthread.php?t=1743535")

I can offer this information.

Grub does not need a video driver nor does it need to know the optimum video settings (screen resolutions) of the monitor. Grub uses a very basic video setting that will work with every monitor without causing damage.

In Ubuntu (I am not sure about other distributions) the X-Server gets the monitor settings from a configuration file in the monitor. The X-server uses the video card to interrogate the monitor.

This is why we do not need to give information regarding screen resolutions and refresh rates when we first install Ubuntu and why we can change monitors without needing to run in low resolution mode first and then run an Add New Hardware utility.

A program called Plymouth puts a splash screen to hide all the kernel messages that are echoed to the screen during the booting of Linux. And a program called LightDM takes over to give a log-in screen.

After log-in the Gnome desktop loads using Compiz as the window manager or compositing manager when we are using Unity 3D. Otherwise Metacity is the compositing manager for Unity 2D

The default video card driver is called Nouveau. It is still very much under development. It is used when we first install and then we can install a proprietary driver if needed, which will be used instead.

Regards.

---

### Post by 23dornot23d on 2012-03-09
> 
Grub does not need a video driver nor does it need to know the optimum  video settings (screen resolutions) of the monitor. Grub uses a very  basic video setting that will work with every monitor without causing  damage.


Are you sure that this is true ..... ?

If it was then the following search would not show any results ....
[https://www.google.com/search?q=grub+stops+on+video+driver](https://www.google.com/search?q=grub+stops+on+video+driver)

[COLOR=Red]**Grub does not need a video driver**[/COLOR]

If it is true .... then no one would need to worry ......

People changing video drivers would not be a problem ......
( grub not needing a video driver ) ......  
It maybe does not if we are we talking about the process grub and not worrying if no boot menu should display for a User to choose the OS.

If a video driver is not needed then why should it stop after a different graphics driver is chosen by the user - if a person sets their best options for a video driver ...

Grub would be unaffected as it does not need a video driver. 

It should work every time - and this is actually what the User needs - and could stop these reports from USERs ..... [[COLOR=Blue]_**Grub cannot display this video mode at boot**_[/COLOR]]("https://www.google.com/search?q=Grub+No+Graphics#hl=en&sclient=psy-ab&q=Grub+cannot+display+this+video+mode+at+boot&oq=Grub+cannot+display+this+video+mode+at+boot&aq=f&aqi=&aql=&gs_sm=3&gs_upl=116l2138l2l2872l10l10l0l0l0l1l439l1688l0.7.1.0.1l10l0&gs_l=serp.3...116l2138l2l2872l10l10l0l0l0l1l439l1688l0j7j1j0j1l10l0&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=accae0551d0d718b&biw=1096&bih=458")

A change to graphics driver should not alter the way grub works either unless the user
specifically asks for it ...... but does the system decide here .... !!!

__________________________________________________________

Not needing a video driver for Grub to display .... would please me ....... 

A User changes a video driver .... this question should be asked ..... or if the initial statement was TRUE then changing the driver should never affect the grub boot menu ....

**So one question may make some users happy after setting up their new display driver ATI or Nvidia.**

[COLOR=Red]**Do you want Grub to use the video driver you have just chosen ...... ? Y/N**[/COLOR]
( If you choose 'Y' you could have problems when restarting the computer a boot menu may not be shown 
[ [_[COLOR=Blue]**some users experience a black screen and white flashing cursor**[/COLOR]_]("https://www.google.com/search?q=some+users+experience+a+black+screen+and+white+flashing+cursor#hl=en&sclient=psy-ab&q=linux+grub+some+users+experience+a+black+screen+and+white+flashing+cursor&oq=linux+grub+some+users+experience+a+black+screen+and+white+flashing+cursor&aq=f&aqi=&aql=&gs_sm=3&gs_upl=28162l32498l0l32681l11l11l0l0l0l2l422l2209l0.6.2.1.1l10l0&gs_l=serp.3...28162l32498l0l32681l11l11l0l0l0l2l422l2209l0j6j2j1j1l10l0&pbx=1&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=accae0551d0d718b&biw=1096&bih=458") ] 
so by choosing N .................... ensures that a boot menu will always appear.

Choosing "Y" could leave you without a boot menu - the next time you restart your computer )

---

