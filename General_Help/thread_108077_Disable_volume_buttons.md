---
title: "Disable volume buttons"
date: 2005-12-25
forum: General Help
---

### Post by stkaplan on 2005-12-25
I am running Kubuntu 5.10 on a Dell Inspiron 8600. I need to have the i8k module loaded in order to get full information about CPU temperature, fans, and such. But when it is loaded, something thinks that my "volume down" button is being held down, so my volume stays at 0, and the volume popup stays on the screen. If I unload the module, everything goes back to normal, but I can't access my fans.

Basically, I'm looking for an easy way to either change the volume control buttons or disable that volume control entirely. Any ideas?

---

### Post by kkass on 2006-01-26
I had the same problem where the audio was always displayed as set to 0%.  Ideally I would like to disable the i8k modules support for the buttons (as this is not important to me).  I have however found a solution for the problem.

It seems that the program 'kmilo' is catching the the key press, and displaying the box.  I simply removed kmilo with the command 'sudo apt-get remove kmilo'.  Alternately you can disable from the following menu.

```
Start Menu / Control Center / KDE Components / Service Manager and in the Startup Services box uncheck Kmilo.
```

Here is the forum I found for reference: [http://www.linuxforum.com/forums/index.php?showtopic=157572](http://www.linuxforum.com/forums/index.php?showtopic=157572)

---

