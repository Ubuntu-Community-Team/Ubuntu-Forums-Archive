---
title: "Another Samba Question"
date: 2005-10-30
forum: Desktop Environments
---

### Post by Nikusan on 2005-10-30
Hi everyone,

I'm having some issues getting samba to behave as I would like it to. I'm sure I'll find the info I need if I keep reading various docs but it'd be great if I could get a quick answer here.

The network here has 3 Ubuntu Breezy and 2 XP Pro SP2 computers. I'd like to get simple read-only file sharing working between all 5 without requiring authentication to access shares. Samba is installed on all 3 Breezy machines.

on Windows:
[LIST]
[*]typing \\computer_name works fine for connecting to the other XP box
[*]typing \\computer_name for a breezy machine requires credentials, and even if I type a user/pass combination that exists on the breezy machine it wont work. It is impossible to leave the user/pass blank.
[/LIST]

on Breezy:
[LIST]
[*]typing smb://computer_name works fine for connecting to an XP box, I am able to view and copy files.
[*]typing smb://computer_name for another breezy machine requires credentials. Oddly, leaving username, domain and password blanks lets me view the shares on that machine, but I cannot open/copy the files.
[/LIST]

I'm not sure what I need to do to get file sharing working without requiring authentication. Do I need to use some kind of guest account on the Breezy boxes? If I do need to use a sort of samba guest account how do I make the Breezy machines transparently provide the required credentials when accessing shares? Any suggestions will be much appreciated.

---

### Post by manicka on 2005-10-30
[http://ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure](http://ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure)

---

### Post by NewbieNik on 2005-10-30
[QUOTE=Nikusan]Hi everyone,

I'm having some issues getting samba to behave as I would like it to. I'm sure I'll find the info I need if I keep reading various docs but it'd be great if I could get a quick answer here.

The network here has 3 Ubuntu Breezy and 2 XP Pro SP2 computers. I'd like to get simple read-only file sharing working between all 5 without requiring authentication to access shares. Samba is installed on all 3 Breezy machines.

on Windows:
[LIST]
[*]typing \\computer_name works fine for connecting to the other XP box
[*]typing \\computer_name for a breezy machine requires credentials, and even if I type a user/pass combination that exists on the breezy machine it wont work. It is impossible to leave the user/pass blank.
[/LIST]

on Breezy:
[LIST]
[*]typing smb://computer_name works fine for connecting to an XP box, I am able to view and copy files.
[*]typing smb://computer_name for another breezy machine requires credentials. Oddly, leaving username, domain and password blanks lets me view the shares on that machine, but I cannot open/copy the files.
[/LIST]

I'm not sure what I need to do to get file sharing working without requiring authentication. Do I need to use some kind of guest account on the Breezy boxes? If I do need to use a sort of samba guest account how do I make the Breezy machines transparently provide the required credentials when accessing shares? Any suggestions will be much appreciated.

Daniel Nixon[/QUOTE]

Getting smb to recognise Windows users was a pain for me too. I was trying on a windows 2000ADS network. At first I set up users on the linux box with the same credentials as the windows users, but when there was 200 pepole plus, that became unworkable.
Then I found this:-

[http://us3.samba.org/samba/docs/man/Samba-Guide/unixclients.html#id2571855](http://us3.samba.org/samba/docs/man/Samba-Guide/unixclients.html#id2571855)

and after a bit of fiddling and adaptation in SWAT I now can set user permissions with Windows accounts allowing administrators full access and domain users read-only, oh happy days.
Now I have squid proxy and dansguardian running too, so I can protect my colleagues from the horrible and nasty stuff thats out there, or ISA server as Microsoft like to call it.

---

### Post by Nikusan on 2005-10-30
Thanks for the replies guys, but there's no domain here, just a simple workgroup. I think I've got everything the way I wanted it now too.

Under the [global] section in /etc/samba/smb.conf

I've changed the line

security = user
to
security = share

and added
guest ok = Yes
to the shares

Thanks for the links :)

---

