---
title: "Run my script when i login with Unity, not when i open a terminal"
date: 2018-01-29
forum: Desktop Environments
---

### Post by Skaperen on 2018-01-29
maybe this belongs in programming.  but i am not sure since this is more about Ubuntu and Unity.

i have a bash script that i would like to have run when i log in with Unity, and can see all the Unity stuff, not when i open a terminal window, and especially not N times when i open N terminal windows.  and remote logins, like via ssh to this host, which do not run Unity, do not count.  only logins that run Unity count.  so if i start up Unity on some virtualized X, the script that user sets up will be run.  the .bashrc script is unsuitable since it runs each time an interactive shell starts up and i doubt it is run by Unity, anyway.  a file to be modified is OK as long as it in the user's home file tree somewhere and owner by thr user.

---

### Post by kostkon on 2018-01-29
You could create a .desktop file for that script file and copy it into the ~/.config/autostart folder, for just one user, or the /etc/xdg/autostart folder, for all users, per the [the Freedesktop.org Desktop Application Autostart Specification]("https://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html").

To enable it you'll need to add the following entry:
```
X-GNOME-Autostart-enabled = true
```
to the .desktop file.

You could, also, add the entry:
```
Onlyshowin = Unity;
```
so that the script will only run when the user logs in Unity, in case the user is able to select another DE during login, e.g. Gnome Shell, or you could support more than one, i.e.:
```
Onlyshowin = Unity;Gnome;
```

Also you can set:
```
Nodisplay = true
```
so that the script will not appear in the dash as an application.

And so on.

You could just c/p a .desktop file from /etc/xdg/autostart and modify it according to your needs.


Hope that helps.

---

### Post by again? on 2018-01-29
Why not check for a graphical environment with the $DISPLAY variable?
```
if [ "$DISPLAY" ]; then
		[COLOR="#696969"]<run some command>[/COLOR]
	else
		echo "Not an X session"
fi
```

---

### Post by Skaperen on 2018-01-30
> **guber2 said:**
> Why not check for a graphical environment with the $DISPLAY variable?
```
if [ "$DISPLAY" ]; then
        [COLOR=#696969]<run some command>[/COLOR]
    else
        echo "Not an X session"
fi
```

so how do i get that to run if that user doesn't open any terminals at all?

---

### Post by Skaperen on 2018-01-30
> **kostkon said:**
> You could create a .desktop file for that script file and copy it into the ~/.config/autostart folder, for just one user, or the /etc/xdg/autostart folder, for all users, per the [the Freedesktop.org Desktop Application Autostart Specification]("https://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html").

To enable it you'll need to add the following entry:
```
X-GNOME-Autostart-enabled = true
```
to the .desktop file.

You could, also, add the entry:
```
Onlyshowin = Unity;
```
so that the script will only run when the user logs in Unity, in case the user is able to select another DE during login, e.g. Gnome Shell, or you could support more than one, i.e.:
```
Onlyshowin = Unity;Gnome;
```

Also you can set:
```
Nodisplay = true
```
so that the script will not appear in the dash as an application.

And so on.

You could just c/p a .desktop file from /etc/xdg/autostart and modify it according to your needs.


Hope that helps.

i have no file called ".desktop" and no directory named "~/.config/autostart folder".  i suspect this file should have some other content, too, but i have no idea what that is.  i think i need an example.  i learn best from examples that i can use and customize.

---

### Post by again? on 2018-01-31
kostkon's method sounds like it may be best for you.

First of all, create the ~/.config/autostart directory if it doesn't exist.
```
mkdir ~/.config/autostart
```

You can use "Startup Applications"(search in the dash) to create the desktop file.
Name your startup, enter the path to your script and add a comment(optional) as shown in pic.
[ATTACH=CONFIG]278396[/ATTACH]

Startup Applications creates an  x-desktop file in ~/.config/autostart.
You can navigate to that directory and view/edit the file.
You may not be able to open by clicking on it.
Drag and drop the file into an open gedit window or open via terminal with 
```
gedit ~/.config/autostart/[COLOR="#B22222"]yourfilename[/COLOR].desktop
```

---

### Post by Skaperen on 2018-02-01
can i use other files i see that have names ending in ".desktop" as starting examples to edit with?  i would like to be able to create this for a user without logging in as that user.  i will be logged in as a non-root user with sudo privileges and want to run a script as root by using sudo, where that script sets up the files for the named user so that the designated script will be run by that user when she logs in on Unity.  the script to be run when she logs in will not output any messages and will not open any windows.  in the future, it may start programs that open windows.

---

### Post by Skaperen on 2018-02-04
what does "search in the dash" mean?  it sounds like "dash" is a thing i need to do this search in, but i have no idea what that means.

---

### Post by again? on 2018-02-04
> **Skaperen said:**
> what does "search in the dash" mean?  it sounds like "dash" is a thing i need to do this search in, but i have no idea what that means.

You mentioned "unity" several times in your first post so I assumed you're using the Unity desktop and would know what the dash is.
dash is the overlay in unity initiated by the Super key where amongst other things you can search for installed apps.
Startup Applications can also be executed via terminal...
```
gnome-session-properties
```

Are you the original user of this account who has over 700 posts dating back to 2015???

---

### Post by Skaperen on 2018-02-09
just because i am using the Unity desktop does not mean i know enough about it to know the terminology and features.  i can get the terminal started,  i can get firefox started.  that's all i've needed the past few years.  i was originally a Slackware user building my own computer hardware and constructing my own installation schemes for CD-R, then DVD-R, then USB memory sticks.  getting up in age i have been transitioning away from that.  now i buy already built computers (from 4 different sources) and have transitioned to Ubuntu.  early on i write my own thing to convert Ubuntu ISO images into memory stick images but loved when i was able to abandon it and just dd the .iso image files to a memory stick and it worked (now i have abandon optical disk media).  during this transition i chose to move to Unity just because it is the default.  i learned a few things, including how to have a 3x3 workspace grid for each user.  but i have never been "into" graphical systems so i really don't understand its concepts.  in contrast, i have written assembly code for over a dozen architectures including a bootloader for one of them.  i've built CDs that can boot on x86 or Sparc and CDs and memory sticks that boot up a 32-bit Linux on older x86 CPUs that can only do 32-bit or a 64-bit Linux on newer x86_64/amd64 CPUs that can run in 64-bit mode.  this should show they layers i am most familiar with.  graphics is not it, for me, though i am interested in writing a graphical app.

as far as i know, i am the only person to use this account on Ubuntu Forums.  is there a reason to believe otherwise?  i have used this account long before 2015, too.

---

