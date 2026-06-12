---
title: "HOWTO: Gutsy screenlets with Compiz widget layer"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by Shimmy on 2007-10-24
Here is how to get Screenlets to work with compiz widget-layer.

First, install screenlets:
> sudo su -c 'echo deb [http://hendrik.kaju.pri.ee/ubuntu](http://hendrik.kaju.pri.ee/ubuntu) gutsy screenlets >> /etc/apt/sources.list'
wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install screenlets
mkdir ~/.config/Screenlets
mkdir ~/.config/autostart

Then start CCSM (System->Preferences->Advanced Desktop Effect Settings), enable the "Regex Matching"-plugin and the "Widget Layer"-plugin. Click on the Widget Layer plugin and choose the "Behaviour"-tab. In the "Widget Windows"-box enter "name=Screenlet.py" (Without quotes).

Now start screenlets manager and add some screenlets.
Press F9 to toggle the widget layer.

---

### Post by apple_and _linux on 2007-10-24
That's so cool!  I thought the idea of a widget layer was neat, but I had no idea how to use it or what to put on it.  Thanks!
Edit: Now I'm wondering how to set different effects for widgets.  It gets annoying having fire on my desktop every time I leave my widgets... I've tryed type=Screenlets.py, type=Widget, and type=Widgets.  Any ideas?

---

### Post by Jrichalot on 2007-10-24
Thank you, that was the missing link for me.
Any idea how to install more interesting ones than "just" the default ones.
Thanks again
Jerome :)

---

### Post by smartboyathome on 2007-10-24
> **apple_and _linux said:**
> That's so cool!  I thought the idea of a widget layer was neat, but I had no idea how to use it or what to put on it.  Thanks!
Edit: Now I'm wondering how to set different effects for widgets.  It gets annoying having fire on my desktop every time I leave my widgets... I've tryed type=Screenlets.py, type=Widget, and type=Widgets.  Any ideas?

I asked about this on the compiz forums, and came up with all the solutions not working. So, for now, I think widgets get the same effects as windows. Also, I tried type=ToolTips (I think they are classified as tooltips), and it didn't work. :(

---

### Post by Shimmy on 2007-10-25
> **apple_and _linux said:**
> That's so cool!  I thought the idea of a widget layer was neat, but I had no idea how to use it or what to put on it.  Thanks!
Edit: Now I'm wondering how to set different effects for widgets.  It gets annoying having fire on my desktop every time I leave my widgets... I've tryed type=Screenlets.py, type=Widget, and type=Widgets.  Any ideas?

I have no effect at all when i close or open my apps, so the screenlets does not either, no fire here.

---

### Post by geeree on 2007-10-25
> **Shimmy said:**
> Here is how to get Screenlets to work with compiz widget-layer.


Thanks, Shimmy. But I seem to have some trouble with some Screenlets and I wonder if the whole scheme is still somewhat buggy. For example, I put up two Launcher widgets — one for Emacs and another for Firefox — but then noticed that the Firefox widget won't work. So I decided to delete the Firefox widget and found that that would delete the Emacs widget too! Next, I decided to remove both of them and start afresh. But when I asked for another Launcher widget, both the Emacs and Firefox launchers reappeared just as before. A second problem is with the Calendar widget. Even if I ask to reappear every time I log in, it won't. This doesn't happen with other widgets that I tried. 

And finally, how about a HOWTO on *writing widgets*! 

Girish.

---

### Post by crotoc on 2007-10-25
I think i have some problems to install this software, please help me ,thanks.
My os is ubuntu 7.10, whether i can use the source you posted above?
i can't carry out the second step, can i use another way to get the key?

---

### Post by Shimmy on 2007-10-25
> **geeree said:**
> Thanks, Shimmy. But I seem to have some trouble with some Screenlets and I wonder if the whole scheme is still somewhat buggy. For example, I put up two Launcher widgets — one for Emacs and another for Firefox — but then noticed that the Firefox widget won't work. So I decided to delete the Firefox widget and found that that would delete the Emacs widget too! Next, I decided to remove both of them and start afresh. But when I asked for another Launcher widget, both the Emacs and Firefox launchers reappeared just as before. A second problem is with the Calendar widget. Even if I ask to reappear every time I log in, it won't. This doesn't happen with other widgets that I tried. 

And finally, how about a HOWTO on *writing widgets*! 

Girish.

I have no idea how to write widgets, but it would be fun to try.
I can't help you with your widget problems, sorry.

---

### Post by Shimmy on 2007-10-25
> **crotoc said:**
> I think i have some problems to install this software, please help me ,thanks.
My os is ubuntu 7.10, whether i can use the source you posted above?
i can't carry out the second step, can i use another way to get the key?

Im also on 7.10, could you explain more in detail what it is that is not working?

---

### Post by fnjordy on 2007-10-25
I see a Gutsy repository is also listed on that site:
```
echo "deb http://hendrik.kaju.pri.ee/ubuntu/ gutsy screenlets" >> /etc/apt/sources.list
```

[http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/)

---

### Post by Shimmy on 2007-10-25
> **fnjordy said:**
> I see a Gutsy repository is also listed on that site:
```
echo "deb http://hendrik.kaju.pri.ee/ubuntu/ gutsy screenlets" >> /etc/apt/sources.list
```

[http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/)

Great, i changed my original post to this.
Thanks

---

### Post by amphoterous on 2007-10-25
Thank you Shimmy! Your directions worked like a charm. =D>

---

### Post by Ruiz on 2007-10-26
I haven't been able to figure out how to install the individual Screenlets. The instructions said ~HOME/.screenlets, but that path doesn't exist.

---

### Post by amphoterous on 2007-10-26
You can make the directory by doing:
```
mkdir ~/.screenlets
```

Then do Places -> Home from the top menu. Press CTRL+H to show hidden folders. Drag and drop the folders into your .screenlets directory!

---

### Post by th3gh05t on 2007-10-29
Hi,

I followed all of your steps, but I get this error when I run "screenlets-manager":

```
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 589, in <module>
    app = ScreenletsManager()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 135, in __init__
    self.connect_daemon()
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 143, in connect_daemon
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 218, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 107, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 121, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

What can I do to this fix this?

---

### Post by th3gh05t on 2007-10-30
Can you help me out Shimmy?

---

### Post by Hexxagon on 2007-10-30
Hi!

I followed the instructions, and didn't get any error messages, but when I hit F9 simply nothing happens...  :(
After a reboot the screen simply gets darker, but no screenlets are appearing, although there are some running...

---

### Post by Zorael on 2007-10-30
Hmm, I can't start the manager. :(

```
zorael@azrael:~$ screenlets-manager
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 23, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 33, in <module>
    import rsvg
ImportError: No module named rsvg
```

What do I need to install?

---

### Post by Source4 on 2007-10-30
I followed the directions exactly and nothing happened.
I am running 7.10 and complitz.

---

### Post by TheScrutinist on 2007-11-05
The repository seems to be down, and that means your computer is trying to download something that isn't there. Does anyone know if there is an alternative repository depot?

EDIT:

You can manually download and install the repository from [here,]("http://compiz.org/Desktop_Screenlets") but instructions regarding that outstrips my abilities. Can anyone give us (me) a hand with that?

---

### Post by salvadorveiga on 2007-11-05
one question guys...sorry if this is such a dumb question but what exactly will "widgets  layer" do ? I had it activated but I guess nothing works... Im not sure what it is supposed to do... and does this only work with screenlets or with gdesklets also ?

thanks

---

### Post by yesjoshyes on 2007-11-05
Thanks Shimmy!  Worked great for me!

---

### Post by Admoseley on 2007-11-10
Can the widget layer consist of gDesklets? How I use gDesklets instead of Screenlets? if at all possible... thanks in advance.

---

### Post by pigbig842001 on 2007-11-10
Hey, it was great. it's working like a charm

---

### Post by Tscheesy on 2007-11-10
> **Zorael said:**
> Hmm, I can't start the manager. :(

```
zorael@azrael:~$ screenlets-manager
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 23, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 33, in <module>
    import rsvg
ImportError: No module named rsvg
```

What do I need to install?

```
librsvg2-bin
python-gnome2-desktop
```was the Solution (Kubuntu7.10) for me..

---

### Post by cherry316316 on 2007-11-10
> **Shimmy said:**
> Here is how to get Screenlets to work with compiz widget-layer.

First, install screenlets:


Then start CCSM (System->Preferences->Advanced Desktop Effect Settings), enable the "Regex Matching"-plugin and the "Widget Layer"-plugin. Click on the Widget Layer plugin and choose the "Behaviour"-tab. In the "Widget Windows"-box enter "name=Screenlet.py" (Without quotes).

Now start screenlets manager and add some screenlets.
Press F9 to toggle the widget layer.

is there a way , i can add some of the small standard ubuntu programs like dictionary , calculator to screenlets with downloading the specific ones for screen lets

and if not , then from where can i get calculator screenlets 

thansk

---

### Post by Shimmy on 2007-11-13
> **cherry316316 said:**
> is there a way , i can add some of the small standard ubuntu programs like dictionary , calculator to screenlets with downloading the specific ones for screen lets

and if not , then from where can i get calculator screenlets 

thansk

You can make any application behave like a screenlet, appearing when showing the compiz-widget-layer.
This will make screenlets and calculator to show in the widget-layer.
> CompizConfig Settings Manager->WidgetLayer->Behaviour->Widget Windows = "name=Screenlet.py | title=Calculator"


---

### Post by cherry316316 on 2007-11-13
> **Shimmy said:**
> You can make any application behave like a screenlet, appearing when showing the compiz-widget-layer.
This will make screenlets and calculator to show in the widget-layer.

hey can u explain what u r doing in " "name=Screenlet.py | title=Calculator"
", cos I did this and i still didnt get calculator when i clicked F9


Thanks

---

### Post by Shimmy on 2007-11-13
> **cherry316316 said:**
> hey can u explain what u r doing in " "name=Screenlet.py | title=Calculator"
", cos I did this and i still didnt get calculator when i clicked F9


Thanks

The "name=Screenlet.py | title=Calculator" is a condition, every application or window that matches this condition, will show up in the widget-layer.
name=Screenlet.py means all applications with the name Screenlet.py.
the pipe char | equals "OR".
title=Calculator means all applications where titlebar says "Calculator".

There is a great doc on this here: [http://wiki.compiz-fusion.org/WindowMatching](http://wiki.compiz-fusion.org/WindowMatching)

---

### Post by SomeGuyDude on 2007-11-13
```
crew@crew-laptop:~$ sudo su -c 'echo deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets >> /etc/apt/sources.list'
[sudo] password for crew:
crew@crew-laptop:~$ wget http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg -O- | sudo apt-key add -
--14:00:26--  http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg
           => `-'
Resolving hendrik.kaju.pri.ee... failed: Name or service not known.
gpg: no valid OpenPGP data found.
crew@crew-laptop:~$ 

```

Eh?

---

### Post by ProfKaramba on 2007-11-15
Is there an way to make some screenlets appear only in the widget layer and others all the time??
That would be just perfect...

EDIT:
I figured out. It's just don't write that line in Appearance settings because screenlets have the option to act like widgets...

---

### Post by Jadd on 2007-11-16
Thanks for that guide!
However, I get this error message: "Unable to connect or launch daemon. Some values may be displayed incorrectly." Does anyone know why?
By the way, does anyone know what the difference between quitting a screenlet and deleting it is?
Oh, and what do enabling Sticky and Widget do?
Thanks everyone!

---

### Post by [Hmk] on 2007-11-16
> **ProfKaramba said:**
> Is there an way to make some screenlets appear only in the widget layer and others all the time??
That would be just perfect...

EDIT:
I figured out. It's just don't write that line in Appearance settings because screenlets have the option to act like widgets...

Where did you find the Appearance settings??? Please tell me because I was trying to do the exact same thing as you. To have the screenlets appear on the desktop all the time without having to click F9. 


 If you click F9 and then right click on a screenlet you can find it there. Properties > options and then select the box treat as a widget. But I still dont see them on my desktop without clicking F9


Thanks.

EDIT: I reset setting in Compiz to default and the screenlets showed up on the desktop without pressing F9. Maybe it just took a restart to fix this issue. I don't know.

---

### Post by Dark Hornet on 2007-11-18
--nice guide...thanks!  :guitar:

---

### Post by SomeGuyDude on 2007-11-18
Still havin' my same problem here, fella. And I really want to try this! What's this "Resolving hendrik.kaju.pri.ee... failed: Name or service not known." malarky?

---

### Post by logonwheeler on 2007-11-19
I can confirm that I received the same message yesterday.. whats going on??

---

### Post by dracker on 2007-11-19
I managed to install it but with this:


Open /etc/apt/sources.list and add:

 deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets

Then run this in a terminal:

 wget [http://download.tuxfamily.org/screenlets/hendrikkaju.gpg](http://download.tuxfamily.org/screenlets/hendrikkaju.gpg) -O- | sudo apt-key add - && sudo apt-get update

and install package 'screenlets' with:

 sudo apt-get install screenlets


Sorry for the format but I'm new in the forum... anyway that worked perfectly, you can see the original instructions in here:
[http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users](http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users)

---

### Post by jgoggles on 2007-11-22
> **dracker said:**
> I managed to install it but with this:


Open /etc/apt/sources.list and add:

 deb [http://download.tuxfamily.org/screenlets](http://download.tuxfamily.org/screenlets) gutsy screenlets

Then run this in a terminal:

 wget [http://download.tuxfamily.org/screenlets/hendrikkaju.gpg](http://download.tuxfamily.org/screenlets/hendrikkaju.gpg) -O- | sudo apt-key add - && sudo apt-get update

and install package 'screenlets' with:

 sudo apt-get install screenlets


Sorry for the format but I'm new in the forum... anyway that worked perfectly, you can see the original instructions in here:
[http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users](http://www.screenlets.org/index.php/FAQ#Installation_instructions_for_Ubuntu_Edgy_Eft.2FFeisty_Fawn.2FGutsy_Gibbon_users)

When I tried that I got this:

 [http://download.tuxfamily.org/screen...endrikkaju.gpg](http://download.tuxfamily.org/screen...endrikkaju.gpg)
           => `-'
Resolving download.tuxfamily.org... 88.191.250.18
Connecting to download.tuxfamily.org|88.191.250.18|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
16:19:45 ERROR 404: Not Found.

gpg: no valid OpenPGP data found.

Any ideas?  It seems like hendrik.kaju.pri.ee is still down as well.

---

### Post by MNICY on 2007-11-23
The problem is, the link is shortened. You NEED to put it in a code box.
These instructoins worked for me:

Open /etc/apt/sources.list 
```
sudo gedit /etc/apt/sources.list
```
and add:

```
deb http://download.tuxfamily.org/screenlets gutsy screenlets
```

Then run this in a terminal:

```
wget http://download.tuxfamily.org/screenlets/hendrikkaju.gpg -O- | sudo apt-key add - && sudo apt-get update
```

and install package 'screenlets' with:

```
sudo apt-get install screenlets
```

---

### Post by BatPenguin on 2007-11-23
Does anybody know what's going on with screenlets.org? I've been trying to get there to get some more screenlets since I just got them working. The default ones don't include weather or disk space monitors which are the ones I need/want. The site seems to be down, does anybody know of a mirror or another site? Thanks.

---

### Post by izhar81 on 2007-11-25
i think it is still down...

any other option instead of screnlets?

---

### Post by rasmusbp on 2007-11-26
Hey, thanks for the how-to! I'm having problems installing though. On the last line of code, I get this error: 

> rasmus@rasmus-laptop:~$ mkdir ~/.config/autostart
mkdir: cannot create directory `/home/rasmus/.config/autostart': File exists


Also, there's no "advanced desktop effect settings" in my preferences menu. 

Can someone help?

Thanks!  : )

Rasmus

---

### Post by BatPenguin on 2007-11-26
> **izhar81 said:**
> i think it is still down...

any other option instead of screnlets?

I used to use gdesklets but they're not as nice looking as these screenlets. I hope the site comes up soon. If anybody has some screenlets already downloaded, please let us know...I have the application itself, I just need a few screenlets (weather and something to monitor disks) so it'd be nice to get them emailed or something if anybody has them. Thanks.

---

### Post by MantenaBr on 2007-11-26
You can try Gnome-Look.org

[http://www.gnome-look.org/index.php?xsortmode=high&xcontentmode=165&page=0](http://www.gnome-look.org/index.php?xsortmode=high&xcontentmode=165&page=0)

---

### Post by BatPenguin on 2007-11-26
Excellent! Thanks

---

### Post by sagara on 2007-11-26
Anybody have any idea how to put some screenlets under the widget layer while others are left out of it?

For example, i would like to always have the clock screenlet on my desktop and then when i hit F9 the weather screenlet would pop out.

I was able to do this in Feisty by setting the **Treat as widget** property on/off.  It doesn't seem to work here...

---

### Post by santiagoward2000 on 2007-11-26
> **sagara said:**
> Anybody have any idea how to put some screenlets under the widget layer while others are left out of it?

For example, i would like to always have the clock screenlet on my desktop and then when i hit F9 the weather screenlet would pop out.

I was able to do this in Feisty by setting the **Treat as widget** property on/off.  It doesn't seem to work here...

That's strange... The **Treat as widget** property works fine in mine... Do you have Compiz-Fusion's **Widgets** plugin enabled?

---

### Post by sagara on 2007-11-26
> **santiagoward2000 said:**
> That's strange... The **Treat as widget** property works fine in mine... Do you have Compiz-Fusion's **Widgets** plugin enabled?

Yeah, i have tried enabling and disabling it but the end result is the same.  All screenlets end up in compiz 's widget layer

Are you setting the widget plug in with ```
name=Screenlet.py
```

---

### Post by santiagoward2000 on 2007-11-26
> **sagara said:**
> Yeah, i have tried enabling and disabling it but the end result is the same.  All screenlets end up in compiz 's widget layer

Are you setting the widget plug in with ```
name=Screenlet.py
```

Ahhh, no! I haven't set anything there. That may be why, you're setting all screenlets as widget. Try leaving it blank, and using the **Treat as widget** property.

---

### Post by sagara on 2007-11-27
Yup, that did the trick! thanks!! =D

---

### Post by santiagoward2000 on 2007-11-27
> **sagara said:**
> Yup, that did the trick! thanks!! =D

You're welcome! :KS

---

### Post by CupAnoodleS on 2007-11-28
> **MNICY said:**
> The problem is, the link is shortened. You NEED to put it in a code box.
These instructoins worked for me:

Open /etc/apt/sources.list 
```
sudo gedit /etc/apt/sources.list
```
and add:

```
deb http://download.tuxfamily.org/screenlets gutsy screenlets
```

Then run this in a terminal:

```
wget http://download.tuxfamily.org/screenlets/hendrikkaju.gpg -O- | sudo apt-key add - && sudo apt-get update
```

and install package 'screenlets' with:

```
sudo apt-get install screenlets
```


ty! it installed...now i need to figure out how to get it to work D:

---

### Post by cherry316316 on 2007-11-28
> **CupAnoodleS said:**
> ty! it installed...now i need to figure out how to get it to work D:

does any one knows , how to add other standard softwares in widget layer, like calculator.

I tried adding the following line in the behavior section of widget layer , but no success so far
```

name=Screenlet.py | title=Calculator

```

---

### Post by santiagoward2000 on 2007-11-28
> **cherry316316 said:**
> does any one knows , how to add other standard softwares in widget layer, like calculator.

I tried adding the following line in the behavior section of widget layer , but no success so far
```

name=Screenlet.py | title=Calculator

```

Actually, with Screenlets is much easier. You don't need to add anything to the line in behavior, or any other option in Compiz-Fusion. All you need to do is open the Screenlets, choose which ones you want to use as widgets, make a right-click on each one of them and choose: **Window/Widget**.

---

### Post by Eric_T on 2007-12-01
Does anyone know how to give an application in the widget layer focus?
I've added a terminal to the layer, and I want it to get focus when I show the widget layer, so that I can start writing commands right away, without clicking it with the mouse first.

---

### Post by Gourgi on 2007-12-07
> **Eric_T said:**
> Does anyone know how to give an application in the widget layer focus?
I've added a terminal to the layer, and I want it to get focus when I show the widget layer, so that I can start writing commands right away, without clicking it with the mouse first.
can you please tell me what name i put in ccsm-->widget layer-->behaviour-->windows widgets so that terminal can appear there ?
i tried name=gnome-terminal but nothing happens 
or if there is another way to add terminal to widgets layer please inform me how

thanks in advance

---

### Post by Sicundercover on 2007-12-08
Thank You these are the first instructions Ive gotten for Ubuntu that worked the first time around. 

Well Written.

---

### Post by fuoco on 2007-12-24
I can't use the repository because there are no debs for my architecture 'powerpc'. Is there any chance I can get access to the source package (so I can build it on my own for my architecture), or even better to the source package repository with the tars and .dsc files?
Thanks a lot!

---

### Post by DarthPooky on 2007-12-30
> **crotoc said:**
> I think i have some problems to install this software, please help me ,thanks.
My os is ubuntu 7.10, whether i can use the source you posted above?
i can't carry out the second step, can i use another way to get the key?
There is.
1. Open this link [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg).
2. In firefox Click File>Save As. 
3. Browse to where you want to save it then click ok.
4. Open a terminal window.
5. Cd to where you saved the file
6. Then type sudo apt-key add hendrikkaju.gpg

---

### Post by Danyl on 2008-01-08
Hi all

I followed this guide but when I hit F9 the widget layer appears but there are no widgets there.

I go into the Screenlets manager (and there are widgets there to choose from) but when I click on Enable or Add, they don't appear.

I'm not sure if this is the problem, but when I type "screenlets-manager" in the terminal, I get the following error:

[B]Error - Please install python image module
DAEMON FOUND![/B]

Can anyone help me get screenlets cranking?

Thanks in advance.

---

### Post by Danyl on 2008-01-09
*bump*

---

### Post by skwerl530 on 2008-01-10
> **Admoseley said:**
> Can the widget layer consist of gDesklets? How I use gDesklets instead of Screenlets? if at all possible... thanks in advance.

Yeah I just set this up on my laptop.  I wanted to use screenlets for various things and I also wanted the Launcherbar from GDesklets.  I wanted them all to appear on the widget layer so I could bring up the bar with the F9 key. 

First I didn't put the "name=screenlet.py" in the ccsm.  instead I right clicked each screenlet and selected "Treat as Widget" in the properties menu of each individual widget.  Next I put "name=gdesklets-daemon" in the "Widget Windows" tab of the CCSM underneath the Widget Layer configuration.  That put both Screenlets and Gdesklets on the widget layer.  Add gedesklets as normal and they should appear on the widget layer.  You will have to edit the source to each desklet to make it pop to the front for the launcher bar it would be this:
```

sudo gedit /usr/share/gdesklets/Displays/starterbar-desklets

```

Change this line:
```

<display anchor="center" window-flages="below, sticky"

```

To this:
```

<display anchor="center" window-flages="above, sticky"

```

That should make the starterbar appear on the widget layer above all other windows when it is invoked with F9.  The final piece I need to figure out is a problem with the background around the starter bar.  It is the same as the desktop image so when I press f9 I get all the pretty widgets except the starterbar has a border of the background image.  It looks a bit crappy.  

I hope this helps!

---

### Post by skwerl530 on 2008-01-10
I gave up trying to get Gdesklets to look right on the Widgets layer.  I used kib-dock instead.  I added "name=kiba-dock" instead and it worked fine.

---

### Post by Colemanvt on 2008-01-15
Nice HOW-TO worked great for me. One hitch though I couldn't get some of my widgets that I installed after the fact to boot up on system startup. After some looking around I found out what to do incase anyone runs into the same problem.

Make sure that the “screenlet name”.py (I.E. facebook.py) has the permission to be run as an executable. to do this... right click on the “screenlet name”.py > properties > permissions tab > and make sure the “Allow executing file as program” box is checked. If it's not checked the screenlet won't start up on system startup which is quite the gay.

---

### Post by lizardopulo on 2008-01-17
thanks so much.. I'll try

---

### Post by vivekh on 2008-01-17
Was having some problems with the install, but now things have started working beautifully! Finally i get my widgets!

---

### Post by Philio on 2008-01-27
Nice guide, thanks :-)

---

### Post by Kevbert on 2008-01-27
Cool. Thanks.

---

### Post by darkwolves on 2008-01-29
Hi all i'm pretty new to linux close to complete novice been able to manage pretty good  with the different Howto's and books I have :lolflag:anyway just install screenlets using this howto on my kubuntu 7.10 gutsy all went well with the install or so i taught now I can't seem get the screenlets manager to load when i click on it it appears to be loading then disappers and if I try and load it from a terminal this is what I get

root:~# 'screenlets-manager'
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/local/share/screenlets-manager/screenlets-manager.py", line 23, in <module>
    import screenlets
  File "/usr/lib/python2.5/site-packages/screenlets/__init__.py", line 33, in <module>
    import rsvg
ImportError: No module named rsvg

Tried 

Code:
librsvg2-bin
python-gnome2-desktop

and got 
bash: librsvg2-bin: command not found
Any help would be greatly appreciated

---

### Post by RTFishUL on 2008-02-04
Halps. I'm pretty sure I enabled all the right things. I have screenlets working and whatnot, but no matter what I do, I can't even activate the widget layer :( hitting F9 gets me nothing.

---

### Post by SanskritFritz on 2008-02-05
> **RTFishUL said:**
> Halps. I'm pretty sure I enabled all the right things. I have screenlets working and whatnot, but no matter what I do, I can't even activate the widget layer :( hitting F9 gets me nothing.Did the screenlet disappear when you right clicked and selected window / widget? That would be the normal behaviour.

---

### Post by mickymouse on 2008-02-27
Very nice thanks alot

---

### Post by LtPitt on 2008-03-13
Aw!

I love this little thingy!

I have just a little question...

Do you think it's possible to bring widgets "more above" than mythtv?

My final dream would be to push a button on my remote command using LIRC and seeing the biggest clock ever :D
Using the remote to push F9 is a problem but I'll solve it later...
I've tried just using the keyboard (while mythtv is running) and I just see the screen getting darker but I see no widgets...
I suppose they're "below"...
I tried to use "Keep above" but no luck...
Any suggestions?

---

### Post by enHuxley on 2008-03-14
To anyone trying to access the screenlets while the site is down, here is some instructions (taken directly from screenlets.org's cache on google: 

[http://64.233.167.104/search?q=cache:QNFNmqDLt8AJ:www.screenlets.org/index.php/FAQ+screenlets+%2Bgutsy&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a](http://64.233.167.104/search?q=cache:QNFNmqDLt8AJ:www.screenlets.org/index.php/FAQ+screenlets+%2Bgutsy&hl=en&ct=clnk&cd=3&gl=us&client=firefox-a)

Here is the quick-instructions,  IF YOU ARE HAVING TROUBLE, I suggest you read through the FAQ from top-to-bottom at the above google cache link, or if the site is ever back up: 

[http://www.screenlets.org/index.php/FAQ](http://www.screenlets.org/index.php/FAQ)

-------(snip)----------------------------------------------------------------------------------------------------
 Using the package manager

    GUI style

        1. Open Synaptic.
        2. Go to: Settings > Repositories > Tab: 3rd party.
        3. Click "Add".
        4. Add the following line:

        deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) gutsy main universe

        5. Click OK, close, etc. until only the main Synaptic window is open. Click "Update" (Far left button)
        6. In Synaptic: Search for "screenlets"
        7. Mark it for installation
        8. "Apply"

        You will be notified by the update manager whenever there's an update to the installed package.

    Console style: 

        echo "deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) gutsy main universe #Gilir's screenlets packages and some stuff you shouldn't use" | sudo tee -a /etc/apt/sources.list

        sudo apt-get update

        sudo apt-get install screenlets

---------(snip)-----------------------------------------------------------------------------------------------------------

Good luck!

---

### Post by munkymac on 2008-03-26
I'm trying to add Rainlendar (which is an exe) to my widget layer. Right now I've got it running on startup, but it lives on the desktop, and I don't understand how to put it on the widget layer. all this talk of screenlets.py hasn't helped me, since it's not a python thing. Any suggestions?

---

### Post by Thug14 on 2008-03-27
thnx a lot, 'twas really helpful

---

### Post by Arlanthir on 2008-03-31
What about if I want the widgets to appear automatically on boot BUT not disappear when I click Show Desktop?

I can make them appear on boot by not applying the widget layer and I can make them not disappear by applying the widget layer. But I want both :S

EDIT: Nevermind that, turned off both widget layer and "hide skip taskbar windows" in compiz config settings manager ;)

---

### Post by lik3n on 2008-04-09
As of April 9th, the command 

wget [http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg](http://hendrik.kaju.pri.ee/ubuntu/hendrikkaju.gpg) -O- | sudo apt-key add - 

no longer works. It's a 404.

---

### Post by StooJ on 2008-04-10
Lik3n

I was trying to install screenlets today & noticed that too.

However, check out enHuxley's instructions further up, that source is still up

---

### Post by alan_daniel on 2008-04-29
There was a post earlier in this thread that doesn't appear to have a solution, and I have the same problem, so I want to bring it back up. I have a terminal set on the widget layer, and I want it to have focus automatically when the widget layer is activated (so that I don't have to click on it first) in order to have a dedicated terminal that's quick and easy to access.

Does anyone know how to go about doing this?

Thanks for any information

---

### Post by cherry316316 on 2008-04-29
> **alan_daniel said:**
> There was a post earlier in this thread that doesn't appear to have a solution, and I have the same problem, so I want to bring it back up. I have a terminal set on the widget layer, and I want it to have focus automatically when the widget layer is activated (so that I don't have to click on it first) in order to have a dedicated terminal that's quick and easy to access.

Does anyone know how to go about doing this?

Thanks for any information

well, i dont know how to do this with screenlets, Shimmy suggested something.
I tried that, but the problem was, i have to have terminal or calculator running always and they became permanent widget.
i.e. I was not able to use them as a normal app. 
If i go and click on the icon, it will go in the widget.

nevertheless, for terminal, there is another way.
you can set a keyboard shortcut.
I have "Ctrl+Alt+Space" as my shortcut to run terminal :)

---

### Post by alan_daniel on 2008-04-29
> **cherry316316 said:**
> well, i dont know how to do this with screenlets, Shimmy suggested something.
I tried that, but the problem was, i have to have terminal or calculator running always and they became permanent widget.
i.e. I was not able to use them as a normal app. 
If i go and click on the icon, it will go in the widget.

nevertheless, for terminal, there is another way.
you can set a keyboard shortcut.
I have "Ctrl+Alt+Space" as my shortcut to run terminal :)

I tried finding that post that Shimmy suggested, but I couldn't...can you possibly direct me or repeat it or something? I'm perfectly fine with having a terminal be a permanent widget, as what I'm currently using as that terminal widget is the Terminal widget found on the Screenlets website. I really just want a terminal that's quickly accessible via a keyboard command without having to open one or switch desktops to one.

---

