---
title: "I don't know how to fix this and i need to"
date: 2006-08-10
forum: Desktop Environments
---

### Post by iammeagain on 2006-08-10
I don't how to fix this, it keeps coming up when i try to install different things. and pressing enter doesnt help, it just keeps doing it](*,) . Thanx in advance.

This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    j2sdk-1_4_2-doc.zip j2sdk-1_4_0-doc-ja.zip j2sdk-1_4_2-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

---

### Post by maniacmusician on 2006-08-10
where are you trying to install them from? source or synaptic? if you want J2SDK, just use Automatix to install it and save yourself the headache. If you for some reason (and it had better be a damn good one lol) dont want to install automatix, i can try and walk you through your current predicament. 

for now, this is how you install automatix. in terminal:

```
sudo gedit /etc/apt/sources.list
```

when the file opens, go down to the very bottom and paste this line at the end:

```
deb http://www.getautomatix.com/apt dapper main
```
save, and close.

then again in terminal, enter these three lines:
```
wget http://www.getautomatix.com/apt/key.gpg.asc
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
```

that imports the keys that you need. now all you have to do is enter these commands:
```
sudo apt-get update
sudo apt-get install automatix
```

after its done installing, run automatix, and voila. yummy linux magic.

---

### Post by iammeagain on 2006-08-10
Well, I have installed Automatix and it seemed like something went wrong but i wasn't sure, i guess something did then, I will try reinstalling it and see what happens.

P.S. I am leaving for about a week tomorrow, just incase i can't reply in time.

---

### Post by iammeagain on 2006-08-10
I have the same problem installing automatix as installing the other programs. 
I'm in no big rush to fix it, so I'm gonna try to download one of those archives it mentions and see what i can do.

lol nvm i have no idea what im doing.

---

### Post by iammeagain on 2006-08-17
Can someone please help me? i'll take the long way around to fix it if i have too, please?

---

### Post by iammeagain on 2006-08-20
maybe my computer is just confused, because i can download and install things, it says it doesn't work but then it does. Its sorta confusing. Anyone have any ideas?

---

