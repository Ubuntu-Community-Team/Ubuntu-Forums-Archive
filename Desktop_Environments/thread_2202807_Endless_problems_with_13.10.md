---
title: "Endless problems with 13.10"
date: 2014-01-31
forum: Desktop Environments
---

### Post by danbuz on 2014-01-31
I use 13.10 and I noticed that is absolute slow for the first 2-3 min after I log in. I mean It opens my file manager for about 25 sec, on 8GB of ram, last gen i5, and 2 gigs of optimus. I know some will say it is the GPU, I walked that way, and installed bumblebee after 3 not successful attempts to install the original drivers (it crashed my system 4 times). The result is that even with bumblebee or not - it is the same slow processing.

After I updated the system this morning it does not open my file manager anymore. After I click on the icon of the folder, It appears for about some milliseconds and then disappears.
Another thing I don't like is the new style of the minimize and close buttons - with some stupid and ugly squares when I put the pointer on it. I would like to brink back the old style with the borders. IS IT POSSIBLE? May be the update is nice for those with only "close" button, but I don't like it.
 
So I should use live boot to copy my files and to try this process for 5th time or there is solution for these 3 problems.

Thanks in advance!

---

### Post by buzzingrobot on 2014-01-31
System Monitor will show you the processes running immediately after a reboot, as well as disk activity.  Perhaps something unusual/broken is consuming resources. Look and see if anything is consistently consuming very high levels of memory or CPU during the time you notice the sluggish behavior.  

Have you added anything to the list of Startup Applications?

Has the system behaved this way since it  was installed?  Is it a stock installation or has it been altered in some fashion?  Did the sluggish behavior begin after an alteration?

If you launch Additional Drivers, it should indicate which video driver is in use.  Bumblebee is intended to manage switching from the Nvidia GPU to the Intel, and vice versa. 

(In Unity, I have the traditional minimize, maximize and close buttons on windows. So should you.)

---

### Post by danbuz on 2014-01-31
the problems appeared after I updated my system. THAT'S IT! Nothing additional added or removed on startup.

I have the minimize maximize and close buttons but they are with different style after the update, which I do not like and I want the old style back - the one with the borders.

Nothing consume my resources, the CPU and RAM usage is normal - about 1,3 CPU AND 780 RAM when no apps opened.

---

### Post by buzzingrobot on 2014-01-31
> **danbuz said:**
> the problems appeared after I updated my system. THAT'S IT! Nothing additional added or removed on startup. 

You updated a stock system? No PPA's?  No core components that you added yourself?  Had you installed a different video driver?

Please confirm you are running *Unity*.

> I have the minimize maximize and close buttons but they are with different style after the update, which I do not like and I want the old style back - the one with the borders.

Have to say I have no idea what you rare referring to here. 

Had you installed a theme that was, perhaps, broken by the update?

> Nothing consume my resources, the CPU and RAM usage is normal - about 1,3 CPU AND 780 RAM when no apps opened.

Did you use System Monitor to see which process were taking the most CPU and the most memory during those few initial moments when the system was sluggish?  And, afterwards, when it is not?  "1,3 CPU" doesn't say much.  Nothing in my System Montor displays that kind of reading. You're looking for a particular process that is consuming a high percentage of CPU, and it will be shown as such, expressed as a percentage.  Memory will be expressed as a simple amount.  Clicking on the heading -- %CPU or Memory -- will alternatively display results in ascending or descending order.

---

### Post by danbuz on 2014-02-02
No broken packages are found via synaptic, no strange processes are consuming resources. Just after update I'm not able to open my file folders!

So I guess It is NO HELP here?

---

### Post by buzzingrobot on 2014-02-02
Help does not come as if by magic.  People here are not clairvoyant.

Your posts have been very vague and without details; you haven't answered questions and you have not responded to suggestions.

---

### Post by danbuz on 2014-02-02
Man what details? If i knew details, I would solve the problem myself, don't you think? I described everything I know - checked synaptic for broken packages - it's fine; CPU and RAM is fine, Everything works fine, except I'm not able to open file manager!

I hoped someone here will suggest me steps to identify the problem or something?

---

### Post by howefield on 2014-02-02
Try opening the file manager via a terminal, might give you some clue as to why it isn't opening.

@buzzingrobot : the thread has an [UbuntuGnome] tag.

---

### Post by buzzingrobot on 2014-02-02
Your complaint was that 13.10 was "absolutely slow" for 2-3 minutes after a restart. Has that been resolved? You were also concerned about video issues. And, you didn't like the window buttons.  Is not being able to open Files now the only current issue?

You haven't confirmed you are using Unity. Or, if you are running a stock system, or have added PPA's, or have added any themes that might affect your issue with the window buttons. And, you haven't provided the results of checking with System Monitor as suggested.

Knowing which desktop interface you are using will tell us which file manager you are using.  Telling us if you have added PPA's or otherwise modified the system might tell us if something that has been added is to blame. Knowing if any processes are taking excessive amounts of CPU or RAM during those first 2-3 minutes after restart might easily identify that problem.

Using Bumblebee would hardly impact a file manager, but knowing the current status of your video driver situation would be helpful in diagnosing the temporary slowness issue, if it, in fact, still exists.

I don't mean to be terse, but you posted a list of problems that may or may not be related.  Declining to answer questions intended to tease out info that might help diagnose those issues won't fix much.

---

### Post by buzzingrobot on 2014-02-02
> **howefield said:**
> Try opening the file manager via a terminal, might give you some clue as to why it isn't opening.

@buzzingrobot : the thread has an [UbuntuGnome] tag.

Ah. Sorry.  I seldom see those.

I will now take my grumpy self out for coffee.

---

### Post by danbuz on 2014-02-02
This is what I get.. Thank you for the suggestion..

```

(nautilus:2687): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files


(nautilus:2687): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed


(nautilus:2687): GLib-GObject-CRITICAL **: g_object_set: assertion 'G_IS_OBJECT (object)' failed


(nautilus:2687): Gdk-ERROR **: The program 'nautilus' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 414 error_code 8 request_code 139 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)



```


> 
[COLOR=#000000]Your complaint was that 13.10 was "absolutely slow" for 2-3 minutes after a restart. Has that been resolved? You were also concerned about video issues. And, you didn't like the window buttons. Is not being able to open Files now the only current issue?[/COLOR]

[COLOR=#000000]You haven't confirmed you are using Unity. Or, if you are running a stock system, or have added PPA's, or have added any themes that might affect your issue with the window buttons. And, you haven't provided the results of checking with System Monitor as suggested.[/COLOR]

[COLOR=#000000]Knowing which desktop interface you are using will tell us which file manager you are using. Telling us if you have added PPA's or otherwise modified the system might tell us if something that has been added is to blame. Knowing if any processes are taking excessive amounts of CPU or RAM during those first 2-3 minutes after restart might easily identify that problem.[/COLOR]

[COLOR=#000000]Using Bumblebee would hardly impact a file manager, but knowing the current status of your video driver situation would be helpful in diagnosing the temporary slowness issue, if it, in fact, still exists.[/COLOR]

[COLOR=#000000]I don't mean to be terse, but you posted a list of problems that may or may not be related. Declining to answer questions intended to tease out info that might help diagnose those issues won't fix much.[/COLOR]


I began with the "list" because I reinstall 6 times this OS man, and I have much personal files I could not afford to lose. I'm kinda pissed off because I feel I can't rely on linux for long term. This is not the first bad surprise for me over time..

---

### Post by danbuz on 2014-02-02
Any suggestions?

---

### Post by howefield on 2014-02-02
Sorry, not really.

But what I would do is now that you have a little more information and are waiting for someone else to come along, I'd take some of the relevant looking stuff from your terminal output and put it into a web search along with the terms ubuntu and gnome or something similar. If I could find something useful then fine, if not I would bin the issue as not fit for purpose.

eg,

```
program 'nautilus' received an X Window System error ubuntu gnome
```

---

### Post by r2ramos on 2014-03-10
> **howefield said:**
> Sorry, not really.

But what I would do is now that you have a little more information and are waiting for someone else to come along, I'd take some of the relevant looking stuff from your terminal output and put it into a web search along with the terms ubuntu and gnome or something similar. If I could find something useful then fine, if not I would bin the issue as not fit for purpose.

eg,

```
program 'nautilus' received an X Window System error ubuntu gnome
```

I have the same problem with nautilus. Installed nemo and it appear to work fine, but couldnt see desktop files. Then de-activated "show desktop icons" and both work well (nautilus and nemo). Then learned how to set nemo to manage desktop files and...surprise! it crashes too!!

Both programs work fin when they are not set to manage desktop files. So, the problem must be something else. !web-searched! as recommended but still no luck. 

Here is what I see in terminal (same thing when natilus was managing desktop files, just change the name):


(nemo:25464): Gdk-ERROR **: The program 'nemo' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 1091 error_code 8 request_code 139 minor_code 4)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
«trap» para punto de parada/seguimiento (`core' generado)


please help

---

