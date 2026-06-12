---
title: "mplayer interferes with realplayer?"
date: 2006-07-02
forum: Desktop Environments
---

### Post by fvs on 2006-07-02
Just did installs of mplayer and realplayer, when I select a realplayer program the mplayer gets there first an it's screws up the reception, How to clear upthis problem?:(

---

### Post by jimbob on 2006-07-02
I assume you are doing this from your browser right?

I had the same problem and cured it by installing the Media Player Connectivity extension for FF which allows me to select which stream is opened by which player.

FF: -> extensions -> miscellaneous -> (search for) media -> Media Player Connectivity 0.5.5
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by fvs on 2006-07-02
[QUOTE=jimbob]I assume you are doing this from your browser right?

I had the same problem and cured it by installing the Media Player Connectivity extension for FF which allows me to select which stream is opened by which player.

FF: -> extensions -> miscellaneous -> (search for) media -> Media Player Connectivity 0.5.5
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR][/QUOTE]
How do I go about that? Sorry to new to know. Thanks

---

### Post by jimbob on 2006-07-02
Sorry - I'll try to be more specific:

1)  In Firefox, click on tools on top menu bar.

2)  Click on extensions.

3)  In the left column click on Miscellaneous.

4)  At the top left you'll see a search bar.  Type in 'media' (without the tick marks).

5)  Scroll down until you see MediaPlayerConnectivity.  Click on it.

6)  Click on the green bar that says "Install Now".

7)  If you have Firefox running, stop it and start a new one.  Now when you click on tools in Firefox you should see a selection at the bottom that says MediaPlayerConnectivity.

8. Select it and click on configure.  At the top where it says Real Media and /usr/bin/X11/gmplayer change that to read /usr/bin/X11/realplay.

  Now when you select a realplayer program only realplay should start for you.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by klytu on 2006-07-06
[QUOTE=fvs]Just did installs of mplayer and realplayer, when I select a realplayer program the mplayer gets there first an it's screws up the reception, How to clear upthis problem?:([/QUOTE]

Also see this thread:

[http://www.ubuntuforums.org/showthread.php?t=200195](http://www.ubuntuforums.org/showthread.php?t=200195)

Make sure to read the whole thread, there are several good Real Player tips there.

---

### Post by Handssolow on 2006-08-24
I want to stop Totem Movie Player being my default media player, use Real Player 10 to play their test clips and to learn more about using Ubuntu.

I've installed Real Player 10 that I found under Graphics in Add/Remove rather than the earlier version of Real Player that's in Sound/Video. I've used FF>Tools> Extensions>Get More Extensions> Misc.(Search for Media)>Downloaded and installed Media Player Connectivity 0.6.3. In FF I've configured Media Connectivity to use Real Player as my chosen player - well for just about most things.

If I return to the Real Player Website and choose to view some test clips, Totem Media Player pops up say that it is the default player and I am unable to play any of Real's test clips.

What do I have to do change my default player.

On second thoughts I also want choice and therefore perhaps if possible no default player. Ok, I expect to have to use Real Player on their website but other media I want to choose.

What's the answer to stopping Totem Media Player from being the default?

---

