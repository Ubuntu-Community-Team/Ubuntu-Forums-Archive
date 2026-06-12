---
title: "Task List Shortcut?"
date: 2009-06-13
forum: General Help
---

### Post by PerfectReign on 2009-06-13
I've searched here and with my buddy, Google, but have not found anything.

The root of my issue is - I am unable to launch firefox for some reason. I closed it, and when I click the icon, nothing happens. Usually - at least in openSUSE - this meant that FF was running and I had to kill it.

I pressed the key combination CTRL + ESC, which should bring up a list of running user programs. However, it didn't do anything.  Realizing I'm used to KDE and fairly new to GNOME, I looked in google. Apparently there is something I'm missing in my search.

What key combination do I press to bring up a list of running applications?

[IMG]http://www.perfectreign.com/stuff/2009/kde_4_task_list.png[/IMG]

---

### Post by synapsys on 2009-06-13
Open a terminal and type 

```
top
```htop is better though

```
sudo apt-get install htop
htop
```

also open a terminal and type

```
firefox
```

and see if it gives you an error message

---

### Post by PerfectReign on 2009-06-13
Thank you.

However, this is 2009 and I'd appreciate not having to downgrade to the CLI whenever possible.  It would be completely ludicrous to have to do so just to get a list of applications. 

On top of that (ignore the pun) one cannot right-click in top and perform actions.

In KDE, anyway, I was able to simply type CTRL+ESC. In Wintendo, I'm able to right-click the taskbar and select task manager.

I did try right-clicking the two - erm - kicker bars on top and bottom. Nothing there either.

Next idea?

---

### Post by drs305 on 2009-06-13
System Monitor shows running apps and with a right click will give you options to close/kill etc. System, Administration, System Monitor: Processes. You can place a link to it on a panel or create a keybinding to open it with the key combination of your choice.

---

### Post by synapsys on 2009-06-13
Don't you mean... upgrade to CLI....?

If you're afraid of the CLI, honestly you will probably be better off with openSUSE or mint.

---

### Post by PerfectReign on 2009-06-13
Erm, no. 

Were this still 1980 and I still using a TRS-80, I'd be happy using the command line. However, I no longer have a dial phone, black and white television or an Izod polo shirt. There should be no reason whatsover to go down to the command line unless one wants to. (I do occasionally go for batch processing photos with imagemagik.)

In any case, I continued searching and found this thread: [http://ubuntuforums.org/showthread.php?t=590654](http://ubuntuforums.org/showthread.php?t=590654)


I used the shortcut key thingy in System>Preferences>Keyboard Shortcuts and now have a somewhat friendly task manager. It unfortunately shows all processes and not just running applications, but it will do for now. (I was able to kill firefox without having to reboot.)

[IMG]http://www.perfectreign.com/stuff/2009/gnome_system_monitor.png[/IMG]

---

### Post by synapsys on 2009-06-13
If you click 'Status' bar at the top it will show running processes at the very top, and sleeping processes below that.

---

### Post by PerfectReign on 2009-06-13
Thank you - did that. What I meant was that I don't want processes necessarily. I want programs (applications) running. I'd then want processes if needed.  

Bit of a kludge but it works.

Off to watch a movie with teh rugrats now. Just got Office 2007 installed via the Wine How-to. (I used to run Crossover office and just wanted to see if this would work.)

:popcorn:

---

