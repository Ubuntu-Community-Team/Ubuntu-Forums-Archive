---
title: "HOWTO: Make Ubuntu Look Like Vista"
date: 2007-12-28
forum: Desktop Effects &amp; Customization
---

### Post by b0rka7a on 2007-12-28
Hi!
This is my modified Ubuntu 7.10 "Gutsy Gibbon" - "Aero"
**[http://ubuntuforums.org/g/index.php?n=1898]("http://ubuntuforums.org/g/index.php?n=1898")**

Here's how you can modify yours to look like mine ;):

Microsoft Segoe UI Font - **[Download]("http://home.arcor.de/salnet/segoe_ui.zip")**
Aero-clone GTK 2.x Theme - **[Download]("http://gnome-look.org/content/download.php?content=57352&id=1&tan=21338614&PHPSESSID=b9a68871d79ab7ec599715ed249c07d9")**
NuoveXT-aero Icons *[Fixed!]* - **[Download]("http://kahns-klan.de/gnome/files/nuoveXT-aero.tar.gz")**
Desktop Screenlets - **[Download]("http://www.compiz.org/Desktop_Screenlets")**
Orb Screenlet *[Updated!]* - **[Download]("http://kahns-klan.de/gnome/files/orb.tar.gz")**

Vista Wallpapers:
**[http://www.winmatrix.com/forums/index.php?showtopic=5254]("http://www.winmatrix.com/forums/index.php?showtopic=5254")**
**[http://www.winmatrix.com/forums/index.php?showtopic=8330]("http://www.winmatrix.com/forums/index.php?showtopic=8330")**
**[http://www.winmatrix.com/forums/index.php?showtopic=12220]("http://www.winmatrix.com/forums/index.php?showtopic=12220")**

The guide I used - **[Make Ubuntu Look Like Vista]("http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html")**
(Use my download links, because some links in that guide don't work)

I hope you like it! :)
Sorry for my bad English... I'm Bulgarian. ;)


*Edit:* I changed my cursor to aero-drop (Aero Mouse Cursor with Drop Shadow) - **[Download]("http://gnome-look.org/content/download.php?content=67833&id=2&tan=63039819")** ; I attached a screenshot...
Info how to install it:
Extract the archive and move the folder to ~/.icons/ .
Go to System > Preferences > Appearance > Theme > Customize > Pointer > aero-drop > Close > Close.
Then, go to ccsm (if you don't have it install it with "sudo apt-get install compizconfig-settings-manager").
General Options > Cursor theme > aero-drop
Close ccsm.
If you need more info you can find it **[here]("http://ubuntu-utah.ubuntuforums.org/showthread.php?p=4030725#post4030725")**.

---

### Post by unclejac on 2007-12-31
Hi b0rka7a, 

Thanks very much for the guide. \\:D/  Worked well for me here.  Though where did you get the Download / Upload running totals from ? I like the look of that.

If you could point me in the right direction that would be great. Cheers!! :cool::cool:

---

### Post by hhhhhx on 2007-12-31
why would you want ubuntu to look like vista?

---

### Post by b0rka7a on 2007-12-31
Hi, uncejac,
here's a link to Net Monitor:
[http://gnome-look.org/content/show.php/Net+Monitor+%28Screenlet%29?content=72013](http://gnome-look.org/content/show.php/Net+Monitor+%28Screenlet%29?content=72013)
It has two modes: the first one is only the speed, and the second one is the speed + total downloaded/uploaded.
Happy New Year!

---

### Post by boboyo on 2007-12-31
thanks man

ill try this:)

---

### Post by money2themax on 2008-01-03
nice i 'm not a fan of vista but i think that was good work man good wrk keep it up u should post this on Gnome-look.org

---

### Post by lolzlolz on 2008-01-03
one comment i have vista and ubuntu and the desktop effects/user interface is way better in ubuntu :D
ubuntu is winning the os race hands down

---

### Post by b0rka7a on 2008-01-03
Thanks! I'm glad you like it :)

---

### Post by axelsvag on 2008-01-07
It looks nice but I got stuck on the third step

3. The Aero-clone theme


Download the Aero-clone theme from Gnome-look.org

--Go to the download site--

Install the Beryl and GTK theme as usual

The download went well but what should I do to install Beryl and GTK theme?

---

### Post by b0rka7a on 2008-01-07
1) For the Beryl theme:
You don't need Beryl. Install Emerald (The Beryl themes are Emerald themes :P)
```
sudo apt-get install emerald
```
Open Emerald by typing in a terminal "emerald-theme-manager", click on Import and find the theme.

2) For the GTK theme:
Go to "System > Preferences > Appearance > Install" and install the theme.

That's all

Edit: I almost forgot!! To apply the Emerald theme, after you imported it, you must type in a terminal
```
emerald --replace
```
,and if sometime emerald crash and you don't have frames on your windows, press Alt + F2 and type "emerald --replace" again.

---

### Post by axelsvag on 2008-01-08
Thank you once again. you are a good friend.

 I ran into new troubles and maybe that is because I have not upgraded yet to 7.10.

2) For the GTK theme:
Go to "System > Preferences > Appearance > Install" and install the theme.

I can find any menu Preferences > Appearance > Install could it be because I still use feisty?

Next trouble

In the tutorial it says  at the fourth row  
4. Icons


Download the nuoveXT-aero iconset

--Go to the download site--

Install the nuoveXT-aero iconset  

How do I install the iconset?

---

### Post by billgoldberg on 2008-01-08
Install icons:
system -> preferences -> appearance

click install. Select the icons set.

Press apply or if costumize and pick the icon set.

---

### Post by b0rka7a on 2008-01-08
"System > Preferences > Appearance > Install Themes" maybe? I don't remember how was in Feisty. :)
Click on "install themes" and select the theme.

---

### Post by extrabigmehdi on 2008-01-08
hi ,
according to the screenshots this look nice,
but I'm definitely missing the glass effect at all windows title bar.
For all those who are bashing Vista,
there is at least one thing that resist to criticism: design.

---

### Post by axelsvag on 2008-01-09
Ok I found one menu in feisty system-->preferences-->theme

if I follow your instruction
> 2) For the GTK theme:
Go to "System > Preferences > Appearance > Install" and install the theme.

the install theme menu does not seem to find any theme to install. If I look in the unpacked file GTK folder I just find a lot a files but none that the installation manager for "theme" like.. Which one should I choose?

---

### Post by talsemgeest on 2008-01-09
You have to select the packed .tar.gz file and it will install the theme from that. Hope I could be of assistance.

---

### Post by axelsvag on 2008-01-09
thak you all for trying but I soon assume that this project is impossible on Feisty.

When I try this 
> cd /path/to/extracted/package
./configure
make
make install

The answer after the ./confugure command is 
```
aco@ubuntu:~/nedladdadefiler/vistalookalike/nuoveXT-aero$ ./configure
bash: ./configure: Filen eller katalogen finns inte

``` The text means The file or catalogue does not exist.

Maybe some else have a clue?

---

### Post by b0rka7a on 2008-01-09
You must install the icon set in the same way you install the GTK theme. Not in a terminal!
Go to "System > Preferences > Themes", click on "Install Theme" and select the icon set.
And why you don't upgrade to Gutsy ?

---

### Post by axelsvag on 2008-01-10
Beacuse I use wubi for the moment and when I read at wubi home page I can see that the 7.10 version is not very stable [HTML]http://wubi-installer.org/[/HTML]. 
In Sweden you still have to use Microsoft to be able to communicate with the authorities. 
I have a few other computer with xubuntu and mythbuntu though, but the reason I use Xubuntu is that it should be light on resources. And the flashy desktop effects seems to heavy on resources.
I would like to try the modern desktopeffects mostly because I want to convince my friends to swap to linux instead of Microsoft.

---

### Post by zipperback on 2008-01-14
I don't really understand people in general wanting to make their system look like Windows Vista, however as far as desktop modifications go, you did a really nice job.

It looks great and very clean.

You did a really nice job on it.

- zipperback
:popcorn:

---

### Post by b0rka7a on 2008-01-14
Thank you :)
Actually (I like this word! :-P), It's like an updated version of this guide: [http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html](http://gnomestyle.blogspot.com/2007/05/make-ubuntu-look-like-vista.html)
Some things in this guide didn't worked and I decided to make a new guide with everything working in it. So I'm only the author of this how-to :)

---

### Post by markp1989 on 2008-01-14
thanks, 

i have 2 questions:

1: how do i change the colour of the font on the panel, cause its black ?

2: i dont have a clue how to use the orb, any one know how i can set it up?

---

### Post by talsemgeest on 2008-01-14
For the font, go to System>Preferences>Appearance and then click on customize. Change whatever colours you want with that.

As for the orb, I also have no idea so I hope someone will help us with that.

Hope I was of some assistance.

---

### Post by markp1989 on 2008-01-14
[http://ubuntuforums.org/showthread.php?t=334570](http://ubuntuforums.org/showthread.php?t=334570)

found that and it done exactly what i want, i just need to get the orb working and il be all good :D

---

### Post by b0rka7a on 2008-01-15
Hi !
Sorry for the late response! :)
Go to the terminal and type:
```
gksudo gedit /etc/apt/sources.list
```
Add the following lines in that file:
```
## Screenlets, Ubuntu Gutsy (7.10):
#deb http://download.tuxfamily.org/screenlets gutsy screenlets
deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets
```
Then go back to the terminal and type:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install screenlets
```
After you install the screenlets, you have to install the orb for the start menu icon. Type:
```
screenlets-manager
```
Click on "Install Screenlet..." and select the orb :)
That's it! Now you just have to adjust it. Remember to unselect "Keep Below", and select "Keep Above" from the Options tab of the orb screenlet!

---

### Post by markp1989 on 2008-01-15
> **b0rka7a said:**
> Hi !
Sorry for the late response! :)
Go to the terminal and type:
```
gksudo gedit /etc/apt/sources.list
```
Add the following lines in that file:
```
## Screenlets, Ubuntu Gutsy (7.10):
#deb http://download.tuxfamily.org/screenlets gutsy screenlets
deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets
```
Then go back to the terminal and type:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install screenlets
```
After you install the screenlets, you have to install the orb for the start menu icon. Type:
```
screenlets-manager
```
Click on "Install Screenlet..." and select the orb :)
That's it! Now you just have to adjust it. Remember to unselect "Keep Below", and select "Keep Above" from the Options tab of the orb screenlet!


thanks for the reply, i am still having problems getting the orb working, when i typer "screenlets-manager" i get a bunch of text that i dont know what it means 

```
mark@mark-desktop:~$ screenlets-manager
/home/mark/.gtkrc-2.0:20: error: invalid string constant "000000", expected valid string constant
/home/mark/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:21: Unable to locate image file in pixmap_path: "Toolbar/toolbar-black.png"
/home/mark/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:24: Background image options specified without filename
/home/mark/.themes/aero-clone/gtk-2.0/gtkrc:187: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/mark/.themes/aero-clone/gtk-2.0/gtkrc:191: Overlay image options specified without filename
Unable to load 'WallpaperClock' from /home/mark/.screenlets/WallpaperClock: No module named Image 
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 589, in <module>
    app = ScreenletsManager()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 133, in __init__
    self.load_screenlets()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 259, in load_screenlets
    info = ScreenletInfo(s, meta['name'], meta['info'], meta['author'], 
TypeError: 'NoneType' object is unsubscriptable
mark@mark-desktop:~$ 

```

---

### Post by b0rka7a on 2008-01-15
I've never had a similar problem :-| I don't know how to fix it. Sorry.
Try google.

---

### Post by markp1989 on 2008-01-15
[http://ubuntuforums.org/archive/index.php/t-592455.html](http://ubuntuforums.org/archive/index.php/t-592455.html) this got the screenlet manager to run, but i need help with the orb, i add it , anbd run it but i dont see anything:S

---

### Post by b0rka7a on 2008-01-15
Maybe you are using the old version of the orb. Use this:
[http://kahns-klan.de/gnome/files/orb.tar.gz](http://kahns-klan.de/gnome/files/orb.tar.gz)

---

### Post by money2themax on 2008-01-15
what's Orb?

---

### Post by alex.de on 2008-01-24
Everything works perfectly except one thing. When I resize the task bar at 32pixel it whitens out. Its all white. When I resize it to 30pixel, it's ok. Since it's not 32pixels, the orb wont show. Any way to fix this? Thanks.

---

### Post by ubacct3 on 2008-02-03
It was difficult getting this theme to work properly, but after I got it working, I really like the new look.  Thank a lot to OP.

---

### Post by Sonic132 on 2008-02-26
Trying to download from within Ubuntu and it's coming up with an error.
Is the mirror down or something? 

Help!

---

### Post by yngens on 2008-02-26
When dragging and dropping The Aero-clone theme to Appearance Preferences - Theme (Ubuntu 7.10)  it gives an error:

The file format is invalid.

I tried to download '57352-aero.tar.gz' from [http://gnome-look.org/content/show.php/Aero-clone?content=57352](http://gnome-look.org/content/show.php/Aero-clone?content=57352) and from this thread, in both cases the same result. 

Could anyone upload a file with the right format, please?

---

### Post by Crafty Kisses on 2008-02-26
I personally hate the Vista look.

---

### Post by money2themax on 2008-02-26
it's nice because it's black [aww...pikachu ([^.^])]

---

### Post by yngens on 2008-02-26
Took me a while to figure out that 57532-aero.tar.gz contains another aero-clone.tar.gz file, which we actually need and which actually should go to the instructions in the first post here.

---

### Post by yngens on 2008-02-27
I've got everything working, except one final thing - when i run a command 'screenlets-manager' it gives en error, though launches screenlets manager:
```

/home/saida/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:21: Unable to locate image file in pixmap_path: "Toolbar/toolbar-black.png"
/home/saida/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:24: Background image options specified without filename
/home/saida/.themes/aero-clone/gtk-2.0/gtkrc:187: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/saida/.themes/aero-clone/gtk-2.0/gtkrc:191: Overlay image options specified without filename
lo
eth0
eth1
0
DAEMON FOUND!
Quit!
```

---

### Post by Cope57 on 2008-02-27
No Vista for me thank you. I already had enough when I beta tested it.

I am pretty happy with my own desktops I create.

[[IMG]http://img86.imageshack.us/img86/9813/screenshotrr9.th.png[/IMG]](http://img86.imageshack.us/my.php?image=screenshotrr9.png) [[IMG]http://img253.imageshack.us/img253/6021/screenshotfd4.th.jpg[/IMG]](http://img253.imageshack.us/my.php?image=screenshotfd4.jpg) [[IMG]http://img160.imageshack.us/img160/8908/screenshotag1.th.png[/IMG]](http://img160.imageshack.us/my.php?image=screenshotag1.png) [[IMG]http://img178.imageshack.us/img178/5263/screenshotow6.th.png[/IMG]](http://img178.imageshack.us/my.php?image=screenshotow6.png) [[IMG]http://img222.imageshack.us/img222/806/screenshotsw3.th.png[/IMG]](http://img222.imageshack.us/my.php?image=screenshotsw3.png) [[IMG]http://img159.imageshack.us/img159/2962/screenshothx2.th.png[/IMG]](http://img159.imageshack.us/my.php?image=screenshothx2.png)  [[IMG]http://img403.imageshack.us/img403/2599/screenshot1as0.th.png[/IMG]](http://img403.imageshack.us/my.php?image=screenshot1as0.png) [[IMG]http://img81.imageshack.us/img81/1126/screenshotst8.th.jpg[/IMG]](http://img81.imageshack.us/my.php?image=screenshotst8.jpg)


But I have made a glass looking theme [**HERE**](http://img524.imageshack.us/my.php?image=screenshottx1.png) though.* Linked because of eight picture limit per post*

---

### Post by appleimac on 2008-03-01
I have a small problem in the top left of the screen the theme does not seem to have worked there and where my name is on the right.

How do I fix this?

See screen attached.

---

### Post by appleimac on 2008-03-02
Anyone how how to fix this problem above.



Cheers

---

### Post by b0rka7a on 2008-03-03
I don't know how to fix them, but you can replace the menu bar with the main menu and remove the user switcher:

To change the Menu Bar to Main Menu:
Right click on the menu bar > Remove from panel > Right click on the panel > Add to panel... > Select Main Menu under Utilities > Click Add

To remove the user switcher:
Right click on the User Switcher > Remove from panel

That's it.

---

### Post by Sonic132 on 2008-03-06
Ok. I have the theme installed. But a lot of it isn't working for me.
I can't get the cursor, iconset, or the orb to work.
Could someone post a walkthough in laymens english for me?
I've followed the guide and downloaded all the applications. Or so I believe.

---

### Post by yizuman on 2008-03-07
Can you redo your instructions for dummies like me?

For example, to create directories and such, can't do it unless I'm a superuser.

Take a look at this page as an example that gives a STEP BY STEP instructions on how to do all this...

[http://ubuntuforums.org/showthread.php?t=613049](http://ubuntuforums.org/showthread.php?t=613049)

He made it so much easier for me to follow the instructions and I was able to install it by following his step by step instructions and copy/paste all the command codes into terminal.

Here's one good example that confuses me...

> Install the Beryl and GTK theme as usual

Question: how?

Thanks

---

### Post by yizuman on 2008-03-07
the file orb.tar.gz is broken.

It said the file format is invalid when I tried to install it.

---

### Post by yizuman on 2008-03-07
I'm confused about this one...

> There is a Ubuntu repository available with the latest version. To use it please add the folowing to your sources.list file:

What source.list file? How do I add it?

Thanks

---

### Post by Vevmesteren on 2008-03-07
just a little rant from my end, how is it thtat Vista has become beautiful, I could not get rid of it fast enought when I got my XPS. Just a question like that...other then that I really too, am impressed, looks just like good ol winBlows, but I really Really REALLY do not want to go back...:)

---

### Post by Terror_Of_Death on 2008-03-08
See Dude...can u make the Orb Installation and screenlet..i just cant get it please help me more


Rock!:guitar::guitar::guitar::guitar:

---

### Post by b0rka7a on 2008-03-08
> **yizuman said:**
> I'm confused about this one...



What source.list file? How do I add it?

Thanks

i dont know, the orb is working fine here...
here's how to edit the sources.list file:
```
gksudo gedit /etc/apt/sources.list
```

@Terror_Of_Death
what ? i couldn't understand... what you cant get ?

---

### Post by Sonic132 on 2008-03-08
> Can you redo your instructions for dummies like me?

For example, to create directories and such, can't do it unless I'm a superuser.

Take a look at this page as an example that gives a STEP BY STEP instructions on how to do all this...

[http://ubuntuforums.org/showthread.php?t=613049](http://ubuntuforums.org/showthread.php?t=613049)

He made it so much easier for me to follow the instructions and I was able to install it by following his step by step instructions and copy/paste all the command codes into terminal.

Here's one good example that confuses me...

Quote:
Install the Beryl and GTK theme as usual
Question: how?

Thanks

Just open Preferences>Appearance>Theme Then drag and drop the theme file into the window.
That's one of the only parts I could get done right.

I still need to get the icon set, orb, and the cursors installed. Also, I don't think it was included but possibly sounds, and a modified logon.ui(Ubuntu equivalent) too.
Shortly before my Windows cratered on me. I had installed a Windows XP to Vista Transformation pack and it came with everything. Anything like that for Ubuntu?

---

### Post by warduke on 2008-03-08
Someone needs to go into that theme and get rid of that windows logo.  Change it to Ubuntu...

[IMG]http://i27.tinypic.com/bbd6t.png[/IMG]

Like take this logo and edit it into that menu bar..  

I'm too stupid to be able to do it.  Though I am smart enough to choose linux over winblows.  :)

---

### Post by Sonic132 on 2008-03-09
Lol nice.

---

### Post by b0rka7a on 2008-03-09
> **warduke said:**
> Someone needs to go into that theme and get rid of that windows logo.  Change it to Ubuntu...

[IMG]http://i27.tinypic.com/bbd6t.png[/IMG]

Like take this logo and edit it into that menu bar..  

I'm too stupid to be able to do it.  Though I am smart enough to choose linux over winblows.  :)

Here's it is:
[http://ubuntuforums.org/showthread.php?t=551313](http://ubuntuforums.org/showthread.php?t=551313)

---

### Post by warduke on 2008-03-09
my best attempt...

[IMG]http://i26.tinypic.com/30athcw.png[/IMG]
[IMG]http://i27.tinypic.com/5mjyp.png[/IMG]

---

### Post by h4mx0r on 2008-03-14
[IMG]http://i29.tinypic.com/25foshx.png[/IMG]

That's the one I'm using. :)

---

### Post by Sonic132 on 2008-03-14
Where did you get yours at h4mx0r?
I think it's prettier and goes with the Vista look better.

---

### Post by h4mx0r on 2008-04-02
I got mine from a google images search or probably xfce looks .org

---

### Post by revelationman on 2008-04-02
My question is why would you ?

---

### Post by Cope57 on 2008-04-02
> **revelationman said:**
> My question is why would you ?

To be like something they hate/dislike?

Good question though.

---

### Post by kroustou on 2008-04-05
cool man!!it will be the fastest vista version :P!

---

### Post by bks on 2008-04-09
This is perfect! Hopefully now I can successfully convert my wife. Thanks!

---

### Post by xdarkxanarchyx on 2008-07-19
This is a good post. I gave my sister a computer and she's freaking out because it's slightly different than the XP machine we have... so I installed IceWM and some themes and made it very much like WinXP. I can't find a boot splash image though and this is important for convincing her that I put Windows on here. Haha. I even called Pidgin "AIM" because that's what she's used to. Followed the guide on [http://celettu.wordpress.com/icewm-guide](http://celettu.wordpress.com/icewm-guide) and found some themes on [www.kde-look.com](www.kde-look.com) and [www.box-look.com](www.box-look.com) Any help with a bootsplash? Even if I can use a still image instead.

---

### Post by xdarkxanarchyx on 2008-07-20
Ah nevermind. I removed splashy and it just showed the text. I explained how and why GNU/Linux is so secure and stable and now I get to put Ubuntu on all the computers in the house! Windows is officially forbidden here. :popcorn:

---

