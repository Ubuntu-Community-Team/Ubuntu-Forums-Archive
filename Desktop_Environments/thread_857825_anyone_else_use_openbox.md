---
title: "anyone else use openbox?"
date: 2008-07-12
forum: Desktop Environments
---

### Post by wolfen69 on 2008-07-12
i just decided to add another hard drive to my computer to run ubuntu minimal with openbox. (i know i can run it along side gnome) i absolutely love how fast and simple it is. it takes a little know-how to get everything set up, (wireless, mounting drives, sound, etc.) because of the lack of easy gui's and pre-installed drivers: like ubuntu) but it seems well worth it. plus, i dont mind the command line. my girlfriend wont like it, so i'll have to reboot back into regular ubuntu after i'm done. i have a few apps open and i'm only using 130mb of ram. in gnome it would be 350+. mind you, im not hurting for speed, (4200 amdX2 and 2gigs ram) but it just feels so damn clean and fast. i can see why people like it.

btw, i know i can look this up, but does anyone know off the top of their head how to add my apps to the right click menu?

---

### Post by Dr Small on 2008-07-12
I use Openbox!
To add things to your menu, edit $HOME/.config/openbox/menu.xml or install obmenu ;)

---

### Post by wolfen69 on 2008-07-12
i just installed obmenu and made a multimedia menu item. saved it, but it doesnt show up when i right click. i even restarted x. what's going on?

---

### Post by wolfen69 on 2008-07-12
also, when you minimize a window, where does it go? how do you get it back?
btw, here is my menu.xml
```
<?xml version="1.0" encoding="utf-8"?>
[B]<openbox_menu xmlns="http://openbox.org/" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://openbox.org/                 file:///usr/share/openbox/menu.xsd">
	<menu id="None-95246" label="Multimedia">
		<item label="vlc">
			<action name="Execute">
				<execute>
					vlc[/B]
				</execute>
			</action>
		</item>
	</menu>
	<menu id="root-menu" label="Openbox 3">
		<item label="Terminal emulator">
			<action name="Execute">
				<execute>
					x-terminal-emulator
				</execute>
			</action>
		</item>
		<item label="Web browser">
			<action name="Execute">
				<execute>
					x-www-browser
				</execute>
			</action>
		</item>
		<!-- This requires the presence of the 'menu' package to work -->
		<menu id="Debian"/>
		<separator/>
		<menu id="client-list-menu"/>
		<separator/>
		<item label="ObConf">
			<action name="Execute">
				<execute>
					obconf
				</execute>
			</action>
		</item>
		<item label="Reconfigure">
			<action name="Reconfigure"/>
		</item>
		<item label="Restart">
			<action name="Restart"/>
		</item>
		<separator/>
		<item label="Exit">
			<action name="Exit"/>
		</item>
	</menu>
</openbox_menu>

```

---

### Post by Dr Small on 2008-07-12
You apparently don't have any panel installed. The window is still there, and still accessible with ALT + TAB. I myself run openbox without a panel, but there are all sorts of different panels you can install. The one that I did like was pypanel.

Here is a good read at the wiki that can probably explain things better for ya then I can :)
[https://help.ubuntu.com/community/Openbox](https://help.ubuntu.com/community/Openbox)

Dr Small

---

### Post by wolfen69 on 2008-07-13
sorry for my ignorance about openbox, but it's relatively new to me and i hav'nt felt like browsing the wikis. but it's no big deal, i'll do some reading on it tomorrow. i'm not sure openbox will become my default, but it's definitely good. (for certain users)

---

### Post by chris4585 on 2008-07-13
you should read this article: [http://urukrama.wordpress.com/openbox-guide/]("http://urukrama.wordpress.com/openbox-guide/")

Openbox is awesome, and for a panel, check out my signature :)

(fbpanel) <3

---

### Post by urukrama on 2008-07-13
If you haven't done so already, I strongly recommend installing obconf and obmenu. They will make your transition to Openbox so much smoother and pleasant!

> **wolfen69 said:**
> i just installed obmenu and made a multimedia menu item. saved it, but it doesnt show up when i right click. i even restarted x. what's going on?

If you create a *new* menu (rather than a submenu of the existing root menu), as you tried to do, you'll have to specify in the rc.xml when to show that menu. 

For example, you can add a key binding for it in the keyboard section of the rc.xml, as follows:

```
<keybind key="A-F3">
      <action name="ShowMenu">
        <menu>**menu id**</menu>
      </action>
    </keybind>
```

This keybinding will show the menu **menu id** when you press Alt+F3. The name of the menu is the menu id it has in your menu.xml (in your example that would be **None-95246**; you can easily rename this in the menu.xml to something more convenient; just make sure you don't have more than one menu with the same id)

The same applies for mousebindings, though there you need to be careful that you put the binding in the right part of the <mouse> section of the rc.xml file: there are sections for window clients, desktop, etc. that govern what happens when you click on the window client, desktop, etc.

See the documentation for more help on [the ShowMenu action]("http://icculus.org/openbox/index.php/Help:Actions#ShowMenu").

You can also add such custom menus to the main menu, by adding the following line to your menu.xml:

```
<menu id="**menu-id**"/>
```

You already have an example of this in the file you posted: the Debian menu. Make sure, though, that the menu id corresponds to a new menu section you've specified in the menu.xml file (the Debian menu is an exception). 

If you don't plan to use the custom menu separately, but only as a submenu of the root menu, I suggest you don't use this method, though, but just add submenus to the main menu through obmenu. It is generally not worth it to create custom menus for a single application, as you wanted to do in the file you posted here.


When you minimize or iconify an application you can de-iconify it with alt-tab: this cycles through the currently open windows, both iconified and un-iconified. Alternatively, you could use a the client-list-menu (middle click on the desktop), or use a panel. For panels, have a look at my Openbox guide (link in signature). It mentions a host of options you can use.

---

### Post by bapoumba on 2008-07-13
Moved to "Desktop Environments".

---

### Post by RedSquirrel on 2008-07-13
Be warned that Openbox is addictive. I played with dwm for a while but find myself using Openbox once again.

In addition to urukrama's detailed guide, I think the documentation on the Openbox website is very well done and worth reading.

[http://icculus.org/openbox/index.php/Main_Page](http://icculus.org/openbox/index.php/Main_Page)

When I use a panel, I always reach for fbpanel.

[http://fbpanel.sourceforge.net/](http://fbpanel.sourceforge.net/)

---

### Post by chris4585 on 2008-07-13
Yeah RedSquirrel fbpanel rocks

what other panel can you output a command? Its awesome for now playing scripts

---

### Post by VMC on 2008-07-13
This is the first I've heard about Openbox. I've been following this thread and followed the link. Very impressive indeed. I read and heard a lot of most all the other DE's and wonder why Openbox hasn't caught on.

I guess the next step is to install it and try it out. I don't usually mess around with the look and feel of my desktop or anything below it. I tend to keep things simple and prefer to learn more of how a system works, than how it looks. Openbox may change my thinking. Thanks.

---

### Post by AnLGP on 2008-07-13
To nitpick I don't believe openbox is a DE but a WM (Window Manager).  I could be wrong, though.

I use openbox on slitaz and JWM on ubuntu.

The reason why I believe WMs don't catch on (openbox, fluxbox, jwm, etc all) is A) some  people really don't like the minimalism B) others don't know they exist C) a different reason.

> 
I guess the next step is to install it and try it out. I don't usually mess around with the look and feel of my desktop or anything below it. I tend to keep things simple and prefer to learn more of how a system works, than how it looks. Openbox may change my thinking. Thanks.

Keeping it simple, indeed.  WMs are the way to go.  If you want to see more simplicity please view the ALAP group in my sig. :)

---

### Post by tel93 on 2008-07-13
Openbox is my favourite WM. When on Debian (NOT on Ubuntu) it is really fast, almost as fast as IceWM

---

### Post by Inxsible on 2008-07-13
My Openbox on Arch rocks !!

Pretty sweet. Easy ! and I can save my resources for the apps that really need it.

On boot, my openbox takes up about 3 to 8 MB.

The total with sshd and conky running comes to about 29-30MB

---

### Post by VMC on 2008-07-13
> **AnLGP said:**
> ...
Keeping it simple, indeed.  WMs are the way to go.  If you want to see more simplicity please view the ALAP group in my sig. :) Thanks I'll check your sig out. By the way, why not Openbox on ubuntu?

---

### Post by AnLGP on 2008-07-13
You can.  Oh I see what you're saying.

I'm used to JWM.

---

### Post by Inxsible on 2008-07-14
> **VMC said:**
> ..... By the way, why not Openbox on ubuntu?I am not sure if that's directed at me or someone else...

But I find Ubuntu to be a lot slower than Debian. Debian Gnome ran pretty quick on my 256 MB RAM machine which had trouble running even Xubuntu.

I have not used Ubuntu or its derivatives since. And I started with Fluxbox on Debian. Then I tried out Arch...which I loved too...different as in nothing is pre-configured for you...

This time I tried Openbox and I have used it since then.

I love both Fluxbox on Debian and Openbox on Arch. - Two of the best distros with two of the best WMs :)

---

### Post by tel93 on 2008-07-21
> **Inxsible said:**
> 
But I find Ubuntu to be a lot slower than Debian. Debian Gnome ran pretty quick on my 256 MB RAM machine which had trouble running even Xubuntu.


That's the reason.

---

### Post by handy on 2008-07-22
I really like Openbox on Arch too.

I'm currently using my initial test install of Arch on my 2nd (testing) machine (because my iMac is in for warranty due to a noisy optical drive) it is still set up with Gnome, it is just like using Ubuntu, except faster & with pacman/yaourt/tupac instead of apt/synaptic.

---

### Post by sixstorm on 2008-07-22
I've dipped my toe in the lake that is "Openbox" but I forced myself to start using it.  It's definitely a whole lot lighter than other WMs but I'm still getting used to it.

---

### Post by minus24 on 2008-07-24
I've been using openbox and pypanel for about a week, on Ubuntu 7.10 and 8.04.1.  As for them being "light", I've not been using Linux for long enough to properly judge that.  Usually, when I check the system monitor, openbox is using about 8MB and pypanel about 5MB of memory.  Is that light?  Both seem very fast.

---

### Post by Korrode on 2008-07-28
> **Inxsible said:**
> But I find Ubuntu to be a lot slower than Debian. Debian Gnome ran pretty quick on my 256 MB RAM machine which had trouble running even Xubuntu.

Over the last few weeks i've dedicated quite a bit of time to achieving a minimalist debian/ubuntu based system.

At first i tried doing a minimal installation from the Debian Lenny/Testing 'netinst' CD. I was immediately impressed by the general speed gain i'd achieved versus a stock Ubuntu installation (with Openbox installed afterward and selected as the WM).

Yet, for various reasons that i wont delve into on this thread (would go way off-topic), I decided i'd prefer the system be Ubuntu at the core (and use the Ubuntu package repos). A closer look at the Ubuntu installation options on the Hardy/8.04 '[Alternate]("http://releases.ubuntu.com/hardy/ubuntu-8.04.1-alternate-i386.iso")' CD showed promise; I could choose a "Command line only" installation, and i could do said installation in "Expert Mode".

Using these options, i was able to perform all desired installation tasks (creating initial user, setting timezone, etc.) but install only the "Base system".
Once booted into this "Base System", iirc it seemed that the installation hadn't set my repo sources correctly in */etc/apt/sources.list*, but, the */etc/apt/sources.list~* file seemed to be setup correctly, so i just:
```
sudo mv /etc/apt/sources.list~ /etc/apt/sources.list
```
Then did:
```
sudo apt-get update
sudo apt-get install xorg
sudo apt-get install openbox openbox-themes obconf obmenu synaptic menu
startx
```

I'm now running Openbox/Xfce4-panel/PCManFM and am **extremely happy** with the environment in regard to both usability and speed/performance.
Even in regard to aesthetics; i installed Nitrogen for easy wallpaper management, (iirc i got the deb package for that from Debian repos... it wasn't in Ubuntu's :-s) and i've found using Openbox's "oldred" theme along with the stock Ubuntu Hardy desktop wallpaper ([warty-final-ubuntu.png]("http://bonq.net/flipp/wp-content/uploads/2008/04/warty-final-ubuntu.png")) to be very appealing.

Also, if you're someone who likes desktop icons, PCManFM can manage your desktop background and display icons, but, i suggest getting the latest version (0.5 stable) from Debian repos as it has an option to "Show menus provided by WM when desktop is clicked"... unless you plan to use a panel's menu (like fbpanel's menu) exclusively.

Anyways, this is turning into more of a blog entry as opposed to a forum post :p
In short;
I agree stock Ubuntu with Openbox installed after is slow, but, it is possible to install Ubuntu in a minimalist fashion, and when done so, i believe there is little performance difference in Debian VS Ubuntu.

EDIT:
Just a note; I'm only a newbie myself with linux (but not with PC hardware/Windows)... perhaps an 'advanced-newbie' these days, but i don't suggest doing a base-only installation to 'beginner-newbies', as your installation will lack much required day-to-day stuff (gksu, etc.) and have no GUI system configuration tools, etc.

---

### Post by RedSquirrel on 2008-07-28
> **Korrode said:**
> Yet, for various reasons that i wont delve into on this thread (would go way off-topic), I decided i'd prefer the system be Ubuntu at the core (and use the Ubuntu package repos). A closer look at the Ubuntu installation options on the Hardy/8.04 '[Alternate]("http://releases.ubuntu.com/hardy/ubuntu-8.04.1-alternate-i386.iso")' CD showed promise; I could choose a "Command line only" installation, and i could do said installation in "Expert Mode".

The Minimal CD is another option for this sort of thing:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Easy-to-follow instructions here:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by picpak on 2008-07-28
> **Korrode said:**
> Also, if you're someone who likes desktop icons, PCManFM can manage your desktop background and display icons, but, i suggest getting the latest version (0.5 stable) from Debian repos as it has an option to "Show menus provided by WM when desktop is clicked"... unless you plan to use a panel's menu (like fbpanel's menu) exclusively.

I for one like lxpanel. It's a good transitioner from gnome-panel, as my lxpanel is set up just like my gnome-panel was. It also loads the standard .desktop menus, no menu editing required.

If you use GDM you can set yourself up a good Logout system for it too. Just copy the logout script from [here](http://crunchbang.org/archives/2008/04/01/openbox-logout-reboot-and-shutdown-script/) and save it as /usr/bin/lxsession-logout:

```
gksudo gedit /usr/bin/lxsession-logout
sudo chmod +x /usr/bin/lxsession-logout
```

All in all it's pretty slick. :)

---

### Post by Inxsible on 2008-07-28
> **Korrode said:**
> ...Snip
Yes Korrode, I always install using the minimal CD for Ubuntu. Or at least I did. 

I was comparing a Ubuntu minimal install as against Debian business iso install with the same WM's installed.


I use Arch as my primary OS now and Debian with Fluxbox is a dual boot on the same machine. Arch seems really fast when compared to Ubuntu and its a rolling release..giving you all the latest software.

Having said that, I would probably not use Arch on a server install - although some people i know, do.

I like the stability of Debian when it comes to servers.

---

### Post by VMC on 2008-07-28
> **Inxsible said:**
> 
I use Arch as my primary OS now and Debian with Fluxbox is a dual boot on the same machine. Arch seems really fast when compared to Ubuntu and its a rolling release..giving you all the latest software.

Having said that, I would probably not use Arch on a server install - although some people i know, do.

I like the stability of Debian when it comes to servers.

Surprisingly, I installed Xfce4 on Arch and then the speed on boot when way down. Xbuntu is faster. I like Arch, maybe I will try and install it using Openbox.

---

### Post by Korrode on 2008-07-29
> **RedSquirrel said:**
> The Minimal CD is another option for this sort of thing:
...Thanks for the links, i'll try installing from that iso soon ^^

> **picpak said:**
> I for one like lxpanel. It's a good transitioner from gnome-panel, as my lxpanel is set up just like my gnome-panel was. It also loads the standard .desktop menus, no menu editing required.

...

All in all it's pretty slick. :)Heh, funny you should mention that, just last night whilst digging around i found the [LXDE]("http://lxde.org/") project... although i didn't quite like the layout of that environment as a whole, i have started using lxpanel :D ...really liking that "Directory Menu" function that displays my home directory in menu format.

> **Inxsible said:**
> Yes Korrode, I always install using the minimal CD for Ubuntu. Or at least I did. 

I was comparing a Ubuntu minimal install as against Debian business iso install with the same WM's installed.Ah ok... well, although i did run Debian Lenny through it's paces when i had it installed, i still wouldn't say my tests were extensive, so i'll take your word for it. :)

> **Inxsible said:**
> I use Arch as my primary OS now and Debian with Fluxbox is a dual boot on the same machine. Arch seems really fast when compared to Ubuntu and its a rolling release..giving you all the latest software.

Having said that, I would probably not use Arch on a server install - although some people i know, do.

I like the stability of Debian when it comes to servers.My housemate is a long time Arch user, and from what i've seen it does look really good (and fast). I'd hope someday i'll move to it myself.
The main thing stopping me atm is Debian/Ubuntu's massive package selection VS Arch's... and a lack of programming skills to compensate.

---

### Post by Inxsible on 2008-07-29
> **VMC said:**
> Surprisingly, I installed Xfce4 on Arch and then the speed on boot when way down. Xbuntu is faster. I like Arch, maybe I will try and install it using Openbox.I am not sure if you already know this...but in Arch, you can have all the daemons run in the background, increasing the boot up speed drastically. You simply have to add an @ sign before the  daemon name in the DAEMON array in rc.conf.

I have all my daemons run in background except the syslog-ng

Also you can allow for some daemons not to start up by adding a ! sign in front of it.

---

### Post by VMC on 2008-07-29
> **Inxsible said:**
> I am not sure if you already know this...but in Arch, you can have all the daemons run in the background, increasing the boot up speed drastically. You simply have to add an @ sign before the  daemon name in the DAEMON array in rc.conf.

I have all my daemons run in background except the syslog-ng

Also you can allow for some daemons not to start up by adding a ! sign in front of it.

Yes, thanks. I knew I should have already mentioned that. Putting them in the background using the "@" made a big difference, but even with that Xfce boots faster in Xbuntu. I'm looking into Openbox.

I noticed a lot of differences between the files used between ubuntu and Arch. I'm thinking its Arch's tie to BSD. I think for one the inittab isn't used in ubuntu. Also ome rc.files are not referenced in ubuntu.
I know ubuntu uses Upstart in place of sysvinit. I'm guessing Arch still uses sysvinit?

---

### Post by mikjp on 2008-07-30
> **Dr Small said:**
> You apparently don't have any panel installed. The window is still there, and still accessible with ALT + TAB. I myself run openbox without a panel, but there are all sorts of different panels you can install. The one that I did like was pypanel.


perlpanel is another possibility.

---

### Post by rtom on 2008-07-31
After 2 years of using Ubuntu I thought Hardy could be slow on my PIII compared to 7.04 so decided to look for something lighter. Now I have Ubuntu 8.04 command line + openbox. Urukrama's blog was a great help, however I had/ still have some troubles:
- after install xorg, dpkg-reconfigure didn't create the Device and Monitor sections in the xorg.conf for the video, so I had to edit manually to make the card working
- I have xterm, but Copy-Paste with Ctrl-C, Ctrl-V isn't working. How to set up this keybinding?
- Feh should display the backgrund pic (in autostart file "eval ('cat $HOME/fehbg') &"), but I got only a gray display. xsession-errors shows only the command, no error.

---

### Post by urukrama on 2008-07-31
> **rtom said:**
> - I have xterm, but Copy-Paste with Ctrl-C, Ctrl-V isn't working. How to set up this keybinding?

Xterm is a bit annoying when it comes to cut/paste, as it uses the PRIMARY selection buffer, whereas the clipboard (which is used when you do Ctrl+c, Ctrl+V etc) uses the SECONDARY. See [this page]("http://www.davidsimmons.com/soft/xtermhacks/") for more info (about half-way down). You can paste highlighted/selected text with a middle mouse click, though. The same applies in urxvt.

> **rtom said:**
> - Feh should display the backgrund pic (in autostart file "eval ('cat $HOME/fehbg') &"), but I got only a gray display. xsession-errors shows only the command, no error.

You have some errors in that command. Try 
```
eval `cat $HOME/.fehbg` &
```

---

### Post by rtom on 2008-07-31
> **urukrama said:**
> 
You have some errors in that command. Try 
```
eval `cat $HOME/.fehbg` &
```

Thanks for the advise, will try it with xterminal! However, feh gives me in command line:

```
tom@desktop-pc:~$ eval 'cat $HOME/.fehbg' &
feh --bg-center "home/tom/.background/pypanel.png
```
and when I type

```
feh --bg-center "home/tom/.background/pypanel.png
```

the answer is changing the prompt to ">" and no reaction for further commands ](*,)

---

### Post by urukrama on 2008-07-31
> **rtom said:**
> Thanks for the advise, will try it with xterminal! However, feh gives me in command line:

```
tom@desktop-pc:~$ eval 'cat $HOME/.fehbg' &
feh --bg-center "home/tom/.background/pypanel.png
```
and when I type

```
feh --bg-center "home/tom/.background/pypanel.png
```

the answer is changing the prompt to ">" and no reaction for further commands ](*,)

It should work when it is in your autostart file. The command I posted will issue the command that is in the ~/.fehbg file, which contains the last desktop set with feh (in your case *feh --bg-center "home/tom/.background/pypanel.png"*)

The reason it you only get a prompt in your terminal is because you are missing a closing quote. Try:

> feh --bg-center "home/tom/.background/pypanel.png**"**

---

### Post by rtom on 2008-07-31
> **urukrama said:**
> The reason it you only get a prompt in your terminal is because you are missing a closing quote. Try:

I was probably blind... Thank you! I added this command to the autostart file and it's working.

The next step would be xterm, I couldn't find any Xresources file in my home directory. Any suggestion, where to look for it?

---

### Post by urukrama on 2008-07-31
You can create that file if you don't have one. It should be /home/USERNAME/.Xdefaults (note the capital X).

---

### Post by cchung85 on 2008-08-09
Oh man Openbox is so hard to setup...

---

### Post by chris4585 on 2008-08-09
> **cchung85 said:**
> Oh man Openbox is so hard to setup...

nah once you get use to it, its second nature, there's only a few things you have to keep in mind, rc.xml menu.xml and autostart.sh and a panel and its config if you want one

---

### Post by cchung85 on 2008-08-16
I know urukrama worked on getting two different gtk profiles, is there an easier way to do so? I'd like to preserve the look of ubuntu so I can still boot into it if something unexpected happens.
I'd like to have a separate look for openbox but everytime I configure it it messes up the fonts and look of gnome...
Anyone solved this problem?

---

### Post by LinuxGuy1234 on 2008-08-21
I plan to install OpenBox on my 2nd Linux system (Linux from Scratch).

---

### Post by ddnev45 on 2008-08-23
I just installed Openbox this morning and I'm really liking it (used blackbox and fluxbox with Redhat 7.x).

---

