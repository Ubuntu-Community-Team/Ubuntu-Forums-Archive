---
title: "using kate in command line.."
date: 2005-05-14
forum: Desktop Environments
---

### Post by improverrr on 2005-05-14
in other distros I can type the "kate /file path/file_name" command and the editor will open in a GUI window.  but in kubuntu I get the following error:

any ideas to fix this?


root@ubuntu:/home/freak # kate /etc/samba/smb.conf
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
kate: ERROR: KUniqueApplication: Registering failed!
kate: ERROR: Communication problem with kate, it probably crashed.

---

### Post by wwwolf on 2005-05-14
[QUOTE=improverrr]in other distros I can type the "kate /file path/file_name" command and the editor will open in a GUI window.  but in kubuntu I get the following error:

any ideas to fix this?


root@ubuntu:/home/freak # kate /etc/samba/smb.conf
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0
kate: ERROR: KUniqueApplication: Registering failed!
kate: ERROR: Communication problem with kate, it probably crashed.[/QUOTE]

For some reason kate does not like being ran as root. You can use kwrite, and nano as root with no problems though.

HTH,

---

### Post by Xian on 2005-05-14
[QUOTE=improverrr]root@ubuntu:/home/freak # kate /etc/samba/smb.conf
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified[/QUOTE]
Try using the sudo command instead of su to root.

$ sudo kate /etc/samba/smb.conf

---

### Post by ceti on 2005-05-14
Try:

1 - Open Konsole
2 - Session --> New Shell
3 - Type--> xhost + [ENTER]
4 - View --> Shell

It should work now.
You may close the 2nd shell:
a - View --> Shell no. 2
b - Session --> Close Session

Cheers

---

### Post by improverrr on 2005-05-14
[QUOTE=ceti]Try:

1 - Open Konsole
2 - Session --> New Shell
3 - Type--> xhost + [ENTER]
4 - View --> Shell

It should work now.
You may close the 2nd shell:
a - View --> Shell no. 2
b - Session --> Close Session

Cheers[/QUOTE]

worked like a champ!  thanks!

---

