---
title: "Firefox Realplayer plugin"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-08-15
I can't get Realplayer to play movies within Firefox.

I have Realplayer installed, and my understanding from the Guides is that the Firefox plugin should have been installed automagically.

I've also tried with Easyubuntu.  This gives me a 'Fix broken packages first' message.  (This is discussed elsewhere in this forum - but I've not seen a satisfactory answer).

Any ideas on a reliable way of installing/enabling the plugin(s) I need?

---

### Post by visionary on 2007-08-11
[COLOR="Blue"]
**TRY THIS PAL...HERE IS HOW!!!!**[/COLOR]

1) Please uninstall any exisiting RealPlayer you have installed in your system
2)Print out this article as we need to close/exit your firefox while we install and configure.....

**So lets start....**

**1)          Uninstalled real player?  Yes?  Proceed to next step......**

**2)         Closed Firefox? yes? Proceed to next step......**

We need to ensure we have the basic codecs,,,
So open up your terminal/console and type....

**3)          sudo apt-get install alsa-oss            **

No Problem?? Good Proceed To Step 4.....

[B]4)      Go to *[http://www.real.com/linux ]("http://www.real.com/linux")* and download the installer to your Desktop. It shoud be a .bin file (eg RealPlayer10GOLD.bin)
[/B]

Open the terminal and navigate to the file "RealPlayer10GOLD.bin". Type 

**5)                  $ cd ~/Desktop**

Verify that the file is executable. If it isn't, type 

** 6)                $ chmod a+x RealPlayer10GOLD.bin**

Run the installer by typing 

** 7)                $ sudo ./RealPlayer10GOLD.bin**

Follow the prompts provided to finish installation.

** Note while Installing RealPlayer ...Take Note of your installation directory. I Installed into my home directory and maybe you could try installing to your home directory rather than to its default desktop.

8) Finally, go to your installed directory. For example, if you installed to /home/XXX/RealPlayer , (Where XXX is the name of your directory) then from your terminal type

**              sudo gedit /home/XXX/RealPlayer/realplay**

[B]and changed line 73 from

                     $REALPLAYBIN “$@”
 
                                   to

                 aoss $REALPLAYBIN “$@”
[/B]

Save and exit....

Now launch Firefox, and try again!!

Cheers All!!!:guitar::popcorn:

Visionary,Singapore

---

### Post by tygern on 2007-08-11
This didn't work for me.  Any other ideas?

I get the error message:  Could not find an appropriate hxplay or realplay in the system path to use as an embedded player.

---

### Post by Gremlinzzz on 2007-08-11
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_RealPlayer_10_Multimedia_Player_.28RealPlayer.29)
heres the codecs i use for movies but i use smplayer and mplayer plugin
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs?highlight=%28codecs%29)

---

### Post by Gremlinzzz on 2007-08-11
maybe this what you need
 Helix plug-in (plays Realplayer files)

    * Read #General Notes
    * Read #How to add extra repositories
    * See also: #How to install Helix Multimedia Player 

sudo apt-get install mozilla-helix-player helix-player

---

