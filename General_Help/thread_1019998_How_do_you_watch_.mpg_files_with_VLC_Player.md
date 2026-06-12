---
title: "How do you watch .mpg files with VLC Player"
date: 2008-12-23
forum: General Help
---

### Post by toms33 on 2008-12-23
I have searched Google and this forum and all the methods DO NOT WORK.

If you now how to do this please respond.

Thank you

---

### Post by taurus on 2008-12-23
What other method have you tried?  And if it didn't work, did you get any error message why it didn't work?

```
vlc filename.mpg
```
Assuming you are in the same directory where the file, filename.mpg, is.

---

### Post by toms33 on 2008-12-23
I have tried the ubuntu restriced codecs, win32codes and changing the sourcelists and respotorys.

The only thing that plays .mpg files "Right out of the box" is MPlayer, which can be found: Applications > Add/Remove > (All available apps) > Search >  MPlayer.

My favorite media players are Real Player and VLC in that order. 
And I would like to get at lease one of them to work. I have tried Helix and Real Player Linux ([www.real.com/linux](www.real.com/linux)) but nothing has worked except MPlayer. I read that .mpg file format is not supported out of the box for the Linux versions of VLC and Real because of licensing, maybe that could explain why all of the methods I have found and tried do not work. 

So if anybody that is reading has had the same problem I am having with VLC or Real and figured out how to get it working please let me know. 

I am using Ubuntu 8.10 by the way.

---

### Post by albinootje on 2008-12-23
> **toms33 said:**
> I have tried the ubuntu restriced codecs, win32codes and changing the sourcelists and respotorys.

The only thing that plays .mpg files "Right out of the box" is MPlayer, which can be found: Applications > Add/Remove > (All available apps) > Search >  MPlayer.

The open source Helix-player cannot play a lot of different file formats by default, so you might forget about that for the moment.
Personally I've never liked RealPlayer, and it's also not so straightforward to install in Linux.

But if you have the w32codecs installed then vlc shouldn't have problems playing mpeg files.
Can you please post the output of the following:
```

dpkg -l|grep codecs
dpkg -l|grep gstreamer

```
My favorite video player is smplayer, really cool!

---

### Post by toms33 on 2008-12-24
Thank you albinootje for your advice. I have tried smplayer before but I get not stop error messages and I am forced to log off Ubuntu to make a SMPlayer error messages stop under Ubuntu 8.10.

I did find a work around to my problem after 3 VMware images later.

The topic title should be called:  How to play .mpg and .mp3 files in MPlayer with loop using Firefox.

Here is my work around to get .mpg and mp3 files to play in firefox with continuous loop. Hopefully this will someone that has had the same problem I did.


How to play .mpg and .mp3 files in MPlayer with loop using Firefox:
---------------------------------------------------------------------
Installing MPlayer:
-------------------
1) Applications > Add/Remove... > Show: All available applications > Search: mplayer > put a check a mark next to MPlayer > (Enable the installation of unsupported and restricted software) Enable > Apply Changes > (Apply the following changes?) Apply > password > Ok > (Downloading and Installing Software) > (New Application has been installed) > Close.


Run MPlayer:
------------
2) Applications > Sound & Video > MPlayer Movie Player > Hit X and close MPlayer. (Now .player will be in your home folder)

Setup MPlayer:
--------------
3) Places > Home Folder > View > Put a check in the box that says "Show Hidden Files" > .mplayer > config > After where it says "#Write your default config options here!" hit enter and make a space > type "loop=0" (without quotes) > Hit the "Save" button > Close cofig > Close .player.


Setup Firefox A:
----------------
4) Firefox > Edit > Preferences > Main > Downloads > Put a check in "Show the downloads window when downloading a file" > Put a check in "Always ask me where to save files" > Close > Close Firefox.


Setup Firefox B (Disable default plugins that don't work):
----------------------------------------------------------
5) Firefox > Edit > Preferences > Main > Manage Add-ons > Plugins > Disable (Windows Media Player Plug-in 10 (compatible;Totem) ) > Disable "Totem Web Browser Plugin 2.24.3" > Disable "Quicktime Plug-in 7.2.0") > Hit X and close Add-ons > Close Firefox Preferences window > Close Forefox.


Setup Firefox C (Setup MPlayer to play .mpg and .mp3)
-----------------------------------------------------
6) Firefox > Address bar > Go to a website that has .mpg or .mp3 files ([www.website.com](www.website.com)) > Click on the .mpg or mp3 file > Firefox will ask you what to do now > Put a check in "Open With" and in the drop down box go down to "Other" > File System > usr > bin > mplayer > Open > Ok

7) Firefox will open .mpeg and .mp3 files now with continuous loop playback.

* Please note that I have setup this up in Ubuntu 8.10 using VMware and not a real machine. If you need any of the disabled Add-ons please see: Firefox > Main > Manage Add-ons > Plugins > Plugin Nmae > Enable > Close.

---

