---
title: "GDM Login Problem"
date: 2011-01-22
forum: Desktop Environments
---

### Post by coronacolada on 2011-01-22
Hi.

I'm playing with an old laptop and threw Maverick onto it yesterday, and installed OpenBox as well. 

Unfortunately, GDM won't allow me to choose which session I want to start into. 

1) there is no gdm.conf OR custom.conf in /etc/gdm -- I never found gdm.conf, and removed custom.conf after changing all values to "false" still didn't work.

2) In System -> Admin -> Login Screen, it only allows me to "Show the screen for choosing.." or "Login as Tom (automatically)". 

3) If I set the login screen to "Show the screen for choosing...", if I type my username (without showing list) or show the list and click my name, it logs me in automatically. 

4) The session select menu DOES appear briefly, when I click on/type my name, but at that point GDM has already begun to log me in. 

5) If I type a bogus username, I'm able to select my session, but I still can't get into it with my default username (as soon as I change the username back to "Tom" it logs me in under the default setting).

Everything I read says to change the values in the .conf files to false, which I did, and it still didn't work, so I deleted them (hoping GDM would generate a new one); now there are no .conf files at all.

this leads me to believe that GDM is pulling a .conf file from somewhere else other than /etc/gdm, but where? 

Any suggestions would be extremely helpful.

Thanks.

---

### Post by Frogs Hair on 2011-01-22
Sounds strange , in login settings make sure the box that allows automatic login is _not_ checked . If it is you will be automatically to the default session . Removing the  auto login will allow selecting between desktop environments . The option will appear on the  under the greeter box after you have entered your name . Select  the desktop option you want before typing your password.

---

### Post by Krytarik on 2011-01-22
The custom/additional configuration is indeed stored in "/etc/gdm/custom.conf", the default configuration is stored in "/etc/gdm/gdm.schemas", which is part of the gdm package, so don't touch the latter.
[http://library.gnome.org/admin/gdm/stable/configuration.html.en](http://library.gnome.org/admin/gdm/stable/configuration.html.en)

Follow Frogs Hair's advice, after entering your username but before entering your password the session options should be given, at the bottom.

---

### Post by coronacolada on 2011-01-23
Right. All of the anything that has to do with auto-login is disabled. All boxes are not checked, and all attributes set to "false" in the config file (which I was able to restore). 

It still logs me in automatically, as soon as I click on (or type) my name, before giving me the chance to choose the session. The session dropdown does appear, but only as it's already logging me into gnome. 

I have tried every combination of settings within the login screen options.

---

### Post by Krytarik on 2011-01-23
That's weird, it should ask for a passwort at manual login.

Try setting up "custom.conf" like this:
```
[daemon]
TimedLoginEnable=false
AutomaticLoginEnable=false
TimedLogin=USERNAME (or blank)
AutomaticLogin=USERNAME (or blank)
TimedLoginDelay=30
DefaultSession=gnome (or blank)
```Also check "gdm.schemas" for any differences against mine, I have the default one:
```
<gdmschemafile>
  <schemalist>
    <schema>
      <key>chooser/Multicast</key>
      <signature>b</signature>
      <default>false</default>
    </schema>

    <schema>
      <key>chooser/MulticastAddr</key>
      <signature>s</signature>
      <default>ff02::1</default>
    </schema>

    <schema>
      <key>daemon/User</key>
      <signature>s</signature>
      <default>gdm</default>
    </schema>

    <schema>
      <key>daemon/Group</key>
      <signature>s</signature>
      <default>gdm</default>
    </schema>

    <schema>
      <key>daemon/AutomaticLoginEnable</key>
      <signature>b</signature>
      <default>false</default>
    </schema>

    <schema>
      <key>daemon/AutomaticLogin</key>
      <signature>s</signature>
      <default></default>
    </schema>

    <schema>
      <key>daemon/TimedLoginEnable</key>
      <signature>b</signature>
      <default>false</default>
    </schema>

    <schema>
      <key>daemon/TimedLogin</key>
      <signature>s</signature>
      <default></default>
    </schema>

    <schema>
      <key>daemon/TimedLoginDelay</key>
      <signature>i</signature>
      <default>30</default>
    </schema>

    <schema>
      <key>debug/Enable</key>
      <signature>b</signature>
      <default>false</default>
    </schema>

    <schema>
      <key>security/DisallowTCP</key>
      <signature>b</signature>
      <default>true</default>
    </schema>

    <schema>
      <key>greeter/Include</key>
      <signature>s</signature>
      <default></default>
    </schema>

    <schema>
      <key>greeter/Exclude</key>
      <signature>s</signature>
      <default>bin,root,daemon,adm,lp,sync,shutdown,halt,mail,news,uucp,operator,nobody,nobody4,noaccess,postgres,pvm,rpm,nfsnobody,pcap</default>
    </schema>

    <schema>
      <key>greeter/IncludeAll</key>
      <signature>b</signature>
      <default>true</default>
    </schema>

    <schema>
      <key>xdmcp/Enable</key>
      <signature>b</signature>
      <default>false</default>
    </schema>

    <schema>
      <key>xdmcp/MaxPending</key>
      <signature>i</signature>
      <default>4</default>
    </schema>

    <schema>
      <key>xdmcp/MaxSessions</key>
      <signature>i</signature>
      <default>16</default>
    </schema>

    <schema>
      <key>xdmcp/MaxWait</key>
      <signature>i</signature>
      <default>30</default>
    </schema>

    <schema>
      <key>xdmcp/DisplaysPerHost</key>
      <signature>i</signature>
      <default>1</default>
    </schema>

    <schema>
      <key>xdmcp/Port</key>
      <signature>i</signature>
      <default>177</default>
    </schema>

    <schema>
      <key>xdmcp/HonorIndirect</key>
      <signature>b</signature>
      <default>true</default>
    </schema>

    <schema>
      <key>xdmcp/MaxWaitIndirect</key>
      <signature>i</signature>
      <default>30</default>
    </schema>

    <schema>
      <key>xdmcp/PingIntervalSeconds</key>
      <signature>i</signature>
      <default>15</default>
    </schema>

    <schema>
      <key>xdmcp/Willing</key>
      <signature>s</signature>
      <default>/etc/gdm/Xwilling</default>
    </schema>

  </schemalist>
</gdmschemafile>
```

---

### Post by coronacolada on 2011-01-23
Thanks for the help. Turns out it was solveable via Sytem -> Admin -> Users & Groups. Way simpler than I was making it. Not a GDM problem at all. 

Replies were muchly appreciated!

---

### Post by Krytarik on 2011-01-23
> **coronacolada said:**
> Thanks for the help. Turns out it was solveable via Sytem -> Admin -> Users & Groups. Way simpler than I was making it. Not a GDM problem at all. 

Replies were muchly appreciated!
Oh, then you had disabled the query for the password at login at all, didn't dare to ask for it, because I didn't know that this is possible at all!

---

### Post by EroomOllor on 2011-07-02
HI Krytarik
 
> **Krytarik said:**
> Oh, then you had disabled the query for the password at login at all, didn't dare to ask for it, because I didn't know that this is possible at all!
 
would you kindly explain how the above 'password at login' is set ? 
 
I think I have similar problems as at start of this thread, and wondered if I need to set something outside of Gnome to login. After my upgrade to 11.04 from 10.10 the desktop became a blank purple sheet. Various trials (such as changing custom.conf, adding to /usr/share/gdm/autostart/LoginWindow/ some .desktop files have changed the 'desktop' ; like i can add g-conf window - but nothing like a 'normal' desktop , and no login screen at all ...
much appreciated!
Eroom

---

### Post by Krytarik on 2011-07-02
EroomOllor, although you say that you already tried manually modifying "/etc/gdm/custom.conf", please try it again the usual, well not that usual, way:

- Create a launcher on your purple sheet style desktop for the command "gdmsetup", therefore just right-click on it and choose the respective options.
- Run it and disable auto-login.
- Switch to a console by pressing Ctrl+Alt+F1, log in there, and enter:
```
sudo service gdm restart
```

Then you should be greeted with the login screen. There you will have some new "Session" options at the bottom panel to choose from, after clicking at your username:

- "Ubuntu": The new Unity interface, which you were logged in by default. See here how to troubleshoot it:
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

- "Ubuntu Classic": The old style Gnome interface you know from your previously used version.

- "Ubuntu Classic (No effects)": The same as above, but without desktop effects, obviously, meaning using Metacity as the window manager instead of Compiz.

Greetings.

---

### Post by EroomOllor on 2011-07-02
Salutations Krytarik, 
much appreciate your hints; however...
 
when I get the purple screen background (with some windows: Configuration editor, Appearance preferences, Preferred Applications ) right-clicking on the background has no effect (none - not even a submenu or sound).
 
I have been looking (this afternoon) at [http://ubuntu4beginners.blogspot.com/2011/06/customize-appearance-of-gnome-panel.html](http://ubuntu4beginners.blogspot.com/2011/06/customize-appearance-of-gnome-panel.html) amongst the other informative pages there...
 
it may not be relevant but on Appearance Preferences it is indicated that "...the required GTK+ theme 'Ambiance' is not installed'... 
 
as I'm not sure if this is crucial or not I'm trying to sort it out...
 
It is very; odd - in tty I can ps -ef | grep gdm  and there are many processess of gmd user - including: metacity, nautilus ... 
 
I am also wondering if it is an 'authorisation' problem -   i've been (trying) to follow
 
[http://library.gnome.org/admin/gdm/stable/configuration.html.en](http://library.gnome.org/admin/gdm/stable/configuration.html.en)
 
and 
 
[http://library.gnome.org/admin/gdm/stable/security.html.en#gdmuser](http://library.gnome.org/admin/gdm/stable/security.html.en#gdmuser)
 
but finding it a labyrinth at the moment!!!
 
Again - really appreciate your work and effort
all the best
Eroom

---

### Post by Krytarik on 2011-07-02
So, you are really stuck on the login screen, and not auto-logging in to a messed-up Unity desktop, as I suspected earlier.

Try reinstalling "gdm":
```
sudo apt-get install --reinstall gdm
```
Also, the missing theme indicates a non-installed "ubuntu-desktop", at least if you didn't mess with the themes, or the upgrade didn't go that well.

Check if the package "ubuntu-desktop" is installed:
```
dpkg -l |grep ubuntu-desktop
```
If it doesn't turn up there, install it:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by EroomOllor on 2011-07-03
Krytarik: greetings; I tried these - but no change. 
 
startx does something different - i just get a purple background with a mouse cursor.
I removed many **_FBDEV(0)_**, **_FBIOPUTCMAP_** errors by booting with a kernel parameter 'nomodeset' ([http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)) (cheers P4man!)
 
not sure of the next approach yet, but have to get outside for a while...
cheers
Eroom

---

### Post by Krytarik on 2011-07-03
This might be a video driver issue, eventually. Please try if a liveCD works, with and without the "nomodeset" parameter.

Also, after trying "startx", check the log files "~/.xsession-errors" and "/var/log/Xorg.0.log" for related error messages.

---

### Post by m.maga on 2011-09-20
> **Krytarik said:**
> Oh, then you had disabled the query for the password at login at all, didn't dare to ask for it, because I didn't know that this is possible at all!

Hi Krytarik,

I've been running under the same problem of coronacolada for months. Sorry, but I didn't get it. I uncheck autologin feature and I did both scenarios: checked and unchecked prompt for password at login. But none worked here. I have ubuntu 10.10 installed. Any clue?

Thank You

---

### Post by Krytarik on 2011-09-20
> **m.maga said:**
> I've been running under the same problem of coronacolada for months. Sorry, but I didn't get it. I uncheck autologin feature and I did both scenarios: checked and unchecked prompt for password at login. But none worked here. I have ubuntu 10.10 installed. Any clue?
So, you aren't asked for your password at login - if autologin is disabled, and password query enabled?

For choosing the session option, remember that you need to click on or enter your username to make those options appear!

Greetings.

---

