---
title: "lightdm greeter banner message"
date: 2013-11-05
forum: Desktop Environments
---

### Post by Lee_Machine on 2013-11-05
All,

I cannot seem to find an easy solution for this using LightDM. It was easy using GDM.

Anyways I need to add a login banner that a user must take positive action (click OK) before they are allow to login Graphically. For example, the lightdm greeter pops up, the user puts in their credentials, and then the banner message pops up. They must then click on before the login process proceeds. 

Any idea How this is done using LightDM? 

Thanks,

Brandon

---

### Post by Lee_Machine on 2013-11-06
For the sake of posting a solution. LightDM does not have a greeter message like GDM2 and 3 does and the GDM 3 version does not work on Ubuntu only a distro with vanilla GNOME 3 like Fedora. So my work around was use the LightDM config file with the option session-startup-script=/etc/lightdm/banner.sh

I wrote a script that makes use of gdialog. For example,

/usr/bin/gdialog --textbox /etc/lightdm/banner.txt 80 80

This creates a text box where the user must click ok to agree with the terms or else they will be logged out.

I wonder what RedHat does for RHEL7? Im assuming it's the vanilla GNOMe 3 so the GDM3 banner should work.

That said, they SHOULD not be that hard considering many customer deployments requires a login banner.

-Brandon

---

### Post by Lee_Machine on 2013-11-07
All,

I cannot seem to find an easy solution for this using LightDM. It is easy using GDM2 and most systems I set up that require one are either Windows or RHEL.

Anyways I need to add a login banner that a user must take positive action (click OK) before they are allowed to login graphically. For example, the lightdm greeter pops up, the user inputs in their credentials, and then the banner message pops up. They must then click ok before the login process proceeds or they will be logged out. 

My current work around is I wrote a script that makes use of gdialog. For example,

/usr/bin/gdialog --textbox /etc/lightdm/banner.txt 80 80

So when a user logs in a text box with an ok and cancel pops up and in the text box is the banner stating the terms and conditions.  If the user clicks cancel they are logged out. 

Using LightDM is there a cleaner way of doing this? It SHOULD not be this hard. It was so easy with GNOME2/GDM2. Why make things harder? 

Thanks,

Brandon

---

### Post by Toz on 2013-11-07
Try this:

Contents of my **/usr/local/bin/question** file:
```
!/bin/bash
zenity --question --title "Terms and Conditions" --text "Do you agree to the terms and conditions?"

```
...I'm using zenity instead (maybe a Xubuntu thing since gdialog doesn't work for me).

Add to the end of **/etc/lightdm/lightdm.conf** the following line:
```
session-setup-script=/usr/local/bin/question
```
...save the file and restart lightdm or reboot.

After you successfully authenticate, that script will be run and the dialog box displayed. By default, on my system if I select No, it dumps me back to the login prompt.

---

### Post by Toz on 2013-11-07
*Duplicate threads merged.*

---

### Post by bart7 on 2014-05-16
Resurrecting an old thread only because this one comes up in a google search for the problem.

Basically I'm in the same boat. I'd like to have a policy document displayed before lightdm starts up. None of the suggested solutions or workarounds work in 14.04 so I've come up with something else

contents of /usr/local/bin/aup.sh
```
#!/bin/bash
false
while [ $? -ne 0 ]; do
  sleep 1
  /usr/bin/gdialog --textbox /etc/issue 80 80
done
unity-greeter

```

This will display /etc/issue with [cancel] [ok] buttons. Clicking cancel jsut re-displays the dialog. Clicking OK breaks the while loop and unity-greeter can run

To get this to happen before the login screen I change
```
Exec=unity-greeter
```
to 
```
Exec=/usr/local/bin/aup.sh
```

in /usr/share/xgreeters/unity-greeter.desktop

I'm sure it could do with some tweaking but this works for our needs.

I'm not sure why the policy banner functionality was not included in the switch from gdm to lightdm, nor why it hasn't been put back. For enterprise and other organisation it's a pretty standard requirement (and one that *nix has had for ages in motd and /etc/issue)

---

### Post by jtniehof on 2014-10-02
This is getting rather teeth-gnashing. The greeter-setup-script does still work for me in 14.04, putting this in a file in /etc/lightdm/lightdm.conf.d/:
```

[SeatDefaults]
greeter-setup-script=/bin/sh -c "until /usr/bin/zenity --width=600 --height=400 --title=WARNING --text-info --filename=/etc/issue; do :; done"

```

This does really funny things to screen locking. If you lock the screen you get the message again, and switching off to another vterm and back brings you back to the unlocked session! I tried bart7's solution, but it has similar behavior. At least this time switching back to the X session vterm brings up a "this session is locked and you'll get the unlock screen soon" message, so it isn't a security problem, it just never shows the unlock dialog.

It looks like the solutions are to write a full GTK+ theme for the gtk greeter or switch to the webkit greeter and theme that out. Neither is terribly well-documented.

---

