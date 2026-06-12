---
title: "HOWTO: (Kubuntu - Gutsy) Separate Kwin &amp; Compiz Sessions"
date: 2007-12-09
forum: Desktop Effects &amp; Customization
---

### Post by kford on 2007-12-09
This post will describe how to create two different sessions in Kubuntu, one that uses Kwin and another that uses Compiz.  It will also automatically initiate the Compiz effect "ADD Helper."  This solution only replaces Kwin or Compiz as the window manager if necessary.

Backstory, if you are interested:  I'm configuring a computer for my 65 year-old-mother, who is fairly new to a computer and only really knows the basics about how to operate one, and I felt that some of the desktop effects offered with Compiz might be useful to her (e.g. the "Zoom effect" if she has a problem reading small text, "ADD Helper" conveys which window is active).  But, since I must manage her computer remotely, I wanted to make sure we could revert easily to Kwin should the need arise (bad package update, etc) so that she doesn't become irreversibly frustrated by a small glitch.

I have found *some* information about how to create separate sessions in KDE, one that uses Kwin and one that employs Compiz, but I didn't find anything recent that I felt explained how to do it simply and clearly.  Most posts tentatively offered an idea that you then had to try.  So here goes.


**1)** Open an editor with root access  (Alt+F2 -> "kdesu kate" , for example).



**2)** Create a new xsession .desktop configuration file for the Compiz session.  I used the the kde.desktop config file as the base file, which is located in /usr/share/xsessions/.  Here is the file I created, which is my current Compiz session file.

```
[Desktop Entry]
Encoding=UTF-8
Type=Application
Exec=/usr/bin/startkde
TryExec=/usr/bin/startkde
Name=KDE with Compiz
Comment=The K Desktop Environment with Compiz, for fancy-schmantzy window effects.
```

Save this file in the /usr/share/xsessions directory.  I named it: "KDEnCompiz.desktop"




**3)** Create *another* .desktop configuration file, this one, however, will be saved to the /usr/share/autostart directory.  Paste the below in it:

```
[Desktop Entry]
Encoding=UTF-8
Exec=/usr/local/bin/CompizOrKwin.sh
Name=Compiz or Kwin
Type=Application
StartupNotify=false
Terminal=false
TerminalOptions=
X-KDE-autostart-after=restore_kmix_volumes
```

Save this file in the /usr/share/autostart directory.  I named it: "CompizOrKwin.desktop"

Note: The last line determines at what point the file will load when KDE is loading.  I decided to have it run after restore_kmix_volumes since I felt this was (very near) the last step of the process.




**4)** Note the Exec line in the above .desktop file.  This script needs be to created.  Open a new file and then copy and paste the below:

```
#!/bin/bash
sleep 2
if [ "$DESKTOP_SESSION" == "KDEnCompiz" ]
then
	if [ `pgrep -c compiz` -eq 0 ]
	then
		compiz --replace &
		killall kwin
	fi
fi

if [ "$DESKTOP_SESSION" == "kde" ]
then
	if [ `pgrep -c kwin` -eq 0 ]
	then
		kwin --replace &
		killall compiz compiz.real
	fi
fi

if [ `pgrep -c compiz` ]
then
	sleep 5
	xsendkeys "Super_L+p"
fi
```

Save the file to "/usr/local/bin/CompizOrKwin.sh" (it must have the same name as the file in the "Exec" line in the above .desktop file).  Once it is saved, open a terminal and enter:  

```
sudo chmod +x /usr/local/bin/CompizOrKwin.sh
```

Please Note: The last "if" statement in the above bash file initiates the ADD Helper effect.  If you don't use the ADD helper, you can delete that section.  If you have changed the key combination that starts ADD Helper, you'll have to modify the "xsendkeys" command.  For this to work, you will likely need to install an additional program.  Open a terminal and enter:

```
sudo apt-get install lineakd
```

This will install "xsendkeys".


More notes on the script:  The "sleep" commands might not be necessary.  Feel free to toy with their lengths.




**5)** Log out and log back in.  KDM should show a new, available session, "KDE with Compiz," which will load Compiz.  The plain old "KDE" session will run Kwin.

---

