---
title: "Keyring manager pass is too old... how do i change?"
date: 2008-01-23
forum: Desktop Environments
---

### Post by oomar on 2008-01-23
I installed ubuntu some time ago and since that time i havent used my wireless card because i accidently turned it off at the bios level. (oops) and then i found that out and now i can see wireless networks!!! lol here is the problem that i have found since then.... when i log on to the network it asks for my systems default password, not that of the wireless network but the original password that i put for the ubuntu install. i have people that KNWO that pass. so i changed it! but i dont know how to change that default pass thing as it puts it. i went from ************* in length to ****************** in length witha  more safe pass... i want to change it so that its the new pass word so that when i enter it in for what ever other reason i need I can use the new one instead of the old.

(i didnt actually type my pass out for the slower ones lol)

please help.... i know how to test whether or not i achieved this... by simply deleting the key in keyring manager and retyping it in.... so ask me if you dont get what i mean cause i REALLY want to fix this.

i have read other posts telling me to delete all keys and then open it up and it will then be in sync with my new pass... well.... im running a up to date system and that is working WORSE than literally hitting it.(hitting it makes my screen stop spasming :lolflag:)

---

### Post by Dngrsone on 2008-01-23
Try going into System, Administration, Users and Groups.  Then change the password for the user root.

---

### Post by oomar on 2008-01-23
that might have done it! thnaks! lol

---

### Post by Dngrsone on 2008-01-23
Happy to be of service.  [IMG]http://i230.photobucket.com/albums/ee303/Dngrs_1/nod.gif[/IMG]

---

### Post by oomar on 2008-01-24
well.... it didnt work... i didnt test it till like.... a mintue ago and it turns out it is still my old password. Who knows how to fix this thing? i mean come on... this is insane!

---

### Post by kyphi on 2008-01-24
To change your password open a terminal and type ```
passwd
``` enter your old password and then when prompted type in your new password.

---

### Post by oomar on 2008-01-24
that changes user pass... it asks for my old password for some reason every time i start my pc up and it goes wireless... it asks for it... EVERYTHING else is my new one... but it still asks for the old one for some reason.

---

### Post by Promaster91 on 2008-01-25
That happens to me too. I change the user pass but the keyring pass is still the same.

---

### Post by TekNullOG on 2008-01-25
I have the same problem too. I changed my password for my user and the root but the keyring password is the same.

At startup, it asks me for my old password every time it searches to connect to a Wi-Fi connection!

Any help would be appreciated.

---

### Post by TekNullOG on 2008-01-25
Found a solution:

Just delete the keyring. It is in your home directory. Use Ctrl+h to show the hidden files, then go to '.gnome2' and then to 'keyrings'. You will find the default keyring there.

---

### Post by kyphi on 2008-01-25
Aha! So you want to know how to change the keyring password NOT the login password.

You can use the same password for both if you wish.  Here is how:

Go to "~/.gnome2/keyrings" and delete (see comment below) the 'default.keyring' file.  In other words, go to Places -> Home Folder -> press Ctrl+h (to show hidden files), scroll to .gnome2, open that file and scroll to keyrings and open that file to find the default.keyring file.

Alternative to deleting that file is to rename it or move it into another folder.

Go to System -> Administration -> Keyring Manager, click on Keyring and then New Keyring and follow the prompts.  Name the new keyring "default" (without the quotes) and enter your passphrase or password (you can make it the same as your login password).  Repeat the password and you are done.

---

### Post by oomar on 2008-01-25
before i do that i would like to know how that helps?

---

### Post by TekNullOG on 2008-02-11
Well, it stopped asking me for my key ring password after doing that and I saw a few people suggest this. I have not experienced any problems since doing so.

Maybe it is not the best solution but it seems to have worked.

---

### Post by doug-M on 2008-03-04
You could try this as well:

[http://ubuntuforums.org/showthread.php?p=4450138#post4450138](http://ubuntuforums.org/showthread.php?p=4450138#post4450138)

---

