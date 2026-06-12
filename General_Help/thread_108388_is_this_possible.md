---
title: "is this possible?"
date: 2005-12-25
forum: General Help
---

### Post by aptsonic on 2005-12-25
in windows xp, i have the ftp for my yahoo hosted webpage set up as a folder on my desktop...

is this possible with ubuntu?

if you could point me in the direction of how to do it that would be awesome.. 

thanks.

---

### Post by Dr. Nick on 2005-12-25
Should Be

Go to Places-Connect to server - and  change service type to "ftp with login" that should mount it and put a shortcut on the desktop for you.

---

### Post by aptsonic on 2005-12-25
[QUOTE=Dr. Nick]Should Be

Go to Places-Connect to server - and  change service type to "ftp with login" that should mount it and put a shortcut on the desktop for you.[/QUOTE]

thanks i didn't know where to start

---

### Post by aptsonic on 2005-12-25
ok new problem... 

every newbie seems to have this problem... 

its owner is set as root... how do i change that?

---

### Post by Dr. Nick on 2005-12-25
[quote=aptsonic]ok new problem... 

every newbie seems to have this problem... 

its owner is set as root... how do i change that?[/quote]

Hmm not sure. Can you view the files and just not modify them, or can you not see anything at all?

---

### Post by aptsonic on 2005-12-26
[QUOTE=Dr. Nick]Hmm not sure. Can you view the files and just not modify them, or can you not see anything at all?[/QUOTE]

well when made the mount at first it said, folder contains no data...

now when ever i try to access the mount, nothing happens, a window pops up asking if u want to cancel.

---

### Post by Dr. Nick on 2005-12-26
Not real sure how the ftp part of connect to server app works. Did it ever ask for your password? If not I would say something is not set right. Click the one you have now and try to unmount it and start again.

Sorry I cant test this myself but my yahoo account doesnt have ftp capabalities anymore

---

### Post by aptsonic on 2005-12-26
[QUOTE=Dr. Nick]Not real sure how the ftp part of connect to server app works. Did it ever ask for your password? If not I would say something is not set right. Click the one you have now and try to unmount it and start again.

Sorry I cant test this myself but my yahoo account doesnt have ftp capabalities anymore[/QUOTE]


it did ask me for my password but that was still of no luck

no prob tho at least i know where to begin, i'll fiddle for a while...

---

### Post by xmastree on 2005-12-26
[QUOTE=aptsonic]now when ever i try to access the mount, nothing happens, a window pops up asking if u want to cancel.[/QUOTE]So **something happens** then. :rolleyes: 
I have my personal ftp as a desktop folder, it works fine. That cancel message appears while it's connecting and downloading the directory listing. It takes less than a minute, but I guess that depends how much is in there.
Be sure you have set nautilus to thumbnail only local images. I think that's the default.

Edit:

> its owner is set as root... how do i change that?The owner of my desktop shortcut is also root,
[ATTACH]4828[/ATTACH]
but I can launch it just fine.

---

### Post by briancurtin on 2005-12-26
[QUOTE=aptsonic]every newbie seems to have this problem... 

its owner is set as root... how do i change that?[/QUOTE]
you dont want to change that
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by aptsonic on 2005-12-26
[QUOTE=xmastree]So **something happens** then. :rolleyes: 
I have my personal ftp as a desktop folder, it works fine. That cancel message appears while it's connecting and downloading the directory listing. It takes less than a minute, but I guess that depends how much is in there.
Be sure you have set nautilus to thumbnail only local images. I think that's the default.
but I can launch it just fine.[/QUOTE]


[http://aptsonic.com/myspace/ubuntuscreens/screen.png]("http://aptsonic.com/myspace/ubuntuscreens/screen.png")

that is the error that comes up...
maybe i'm not logging in correctly... wrong password or something... gonna test that idea...

---

### Post by Dr. Nick on 2005-12-26
Hmm are you typing the "ftp" in the server box or just the p3... I could be wrong but for some reason that address its connecting to in your pic just doesnt seem right, If your not already dont type ftp in the server box, just set the type to ftp with login

---

### Post by xmastree on 2005-12-26
It says couldn't display **all** the contents. What happens when you click ok, soes it show **any?**

EDIT: Dr.Nick: Good point. In the location, mine says [ftp://ftp.foobar.com](ftp://ftp.foobar.com)

Maybe the **ftp://** ought to be in there?

---

### Post by aptsonic on 2005-12-26
sadly i am using the right user name and password...

and nope it doesn't show anything..

[QUOTE=xmastree]It says couldn't display **all** the contents. What happens when you click ok, soes it show **any?**

EDIT: Dr.Nick: Good point. In the location, mine says [ftp://ftp.foobar.com](ftp://ftp.foobar.com)

Maybe the **ftp://** ought to be in there?[/QUOTE]

gonna try that tho... 

did u enter it like this "//ftp.foobar.com" or as "ftp://ftp.foobar.com"?

the reason i ask is because the way my host tells me to connect it is "ftp.p3.webhosting.yahoo.com", the "ftp:" that is in the pictures is added by the mount.

---

### Post by aptsonic on 2005-12-26
"//ftp.foobar.com"

that was a bad idea, it crashed nautilus... 

lol.

it mounted the folder as "(null)"...

---

### Post by aptsonic on 2005-12-26
[QUOTE=aptsonic]"//ftp.foobar.com"

that was a bad idea, it crashed nautilus... 

lol.

it mounted the folder as "(null)"...[/QUOTE]

no luck...

---

### Post by aptsonic on 2005-12-26
[QUOTE=Dr. Nick]Hmm are you typing the "ftp" in the server box or just the p3... I could be wrong but for some reason that address its connecting to in your pic just doesnt seem right, If your not already dont type ftp in the server box, just set the type to ftp with login[/QUOTE]


i'm have it set up as ftp with login... 

tried it as...

ftp.p3.webhosting.yahoo.com (this is what yahoo says to use)
p3.webhosting.yahoo.com (doesn't work at all)
//ftp.p3.webhosting.yahoo.com(gets labeld as null, and crashed)
[ftp://ftp.p3.webhosting.yahoo.com](ftp://ftp.p3.webhosting.yahoo.com) (same as 2)
[ftp://p3.webhosting.yahoo.com(same](ftp://p3.webhosting.yahoo.com(same) as 2)

---

### Post by aptsonic on 2005-12-26
just took this screen shot...

i highlighted something i thought was interesting.

[http://aptsonic.com/myspace/ubuntuscreens/hmmm.png]("http://aptsonic.com/myspace/ubuntuscreens/hmmm.png")

my first thought was maybe i used the wrong password, but i experimented and when i use the wrong password the folder doesn't even open, so its not that...

so now that i've tried everything i can think of...
is yahoo blocking my computer because its linux?
or is it on my end?

---

### Post by Dr. Nick on 2005-12-26
hmm dont think yahoo would block you due to linux. Check you email though and make sure they didnt suspend your account due to activity. Ive messed with my geocites page some and they halted it because they thougt is was being hacked, maybe youve had it right but they disaled it.

Also you may try a standalone ftp client like gftp and see if that works at all.

---

### Post by aptsonic on 2005-12-26
ok this is weird now...

i went on to synaptic and downloaded gftp... it is able to see everything on the remote ftp..

---

### Post by sas171 on 2005-12-30
Its all good, the connection works fine, but where does it mount? Can I work with console and shared folders? The console ftp tool is not my thing.

*** Edit: There is a nice [How-to]("http://www.ubuntuforums.org/showthread.php?p=615323") work with remote folders and console.

---

