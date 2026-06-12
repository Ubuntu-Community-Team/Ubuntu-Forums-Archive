---
title: "fileserver and symlinks"
date: 2006-08-15
forum: Desktop Environments
---

### Post by Redeyes_Gambit on 2006-08-15
}{i,

I have a question regarding how exactly I could access my fileserver from easytag/any other program.

See, in this case, I want to edit the ID3 tag info on a bunch of MP3's I have stored on my home fileserver with the path of: smb://192.168.2.111/FreeNAS. 

Unfortunately, if I copy/paste that address, easy tag cant find it.

So what I would like to do (I guess) is create a symlink from /home/(user name)/my_stuff/My Music to the fileserver's music directory of smb://192.168.2.111/FreeNAS/RGs_Stuff/Musica.

However, there are a few things I need to know. For instance:

1. Lol, is it even possible to symlink the two?

2. I am on a laptop, and so I will not always be connected to the fileserver. Will this cause complications?

3. What syntax will I need to use to create the link? I tried reading the manpage, and looking on the net but have yet to find a place that explains it thoroughly.

3. Does nautilus have easy way to make symlinks (like making "shortcuts" in windows?)? If not, is there a way to give it this ability?

thanks for your help :)

RG

---

### Post by llamakc on 2006-08-15
You want to mount the samba share to your Desktop.

---

### Post by llamakc on 2006-08-15
So you do:
```

mount -t smb 192.168.2.111/FreeNAS/RGs_Stuff/Musica ~/Desktop/MyMusic 
```

---

### Post by Redeyes_Gambit on 2006-08-15
Ok, tried that and got:

mount: unknown filesystem type 'smb'

---

### Post by llamakc on 2006-08-15
You type the command into a terminal.

---

### Post by Redeyes_Gambit on 2006-08-15
I did. Got "mount: unknown filesystem type 'smb'"

---

### Post by llamakc on 2006-08-15
My bad:

-t smbfs instead. And here's a great page:

[https://help.ubuntu.com/community/SettingUpSamba#head-ba788901ae70dbe3b5bede46397c3e29d7df5ce8](https://help.ubuntu.com/community/SettingUpSamba#head-ba788901ae70dbe3b5bede46397c3e29d7df5ce8)

Which shows a different way.

---

### Post by Redeyes_Gambit on 2006-08-15
ok, replaced the smb with smbfs and got another error:

mount: wrong fs type, bad option, bad superblock on 192.168.2.111/FreeNAS/RGs_Stuff/Musica,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Redeyes_Gambit on 2006-08-15
I have encountered that error before, when trying to make the server mounted at startup through fstab. eventually I just stumbled across the button under "places" that said "connect to server" and all I had to do is input the sharename etc and viola! working share.

never did figure out how to mount with fstab

---

### Post by llamakc on 2006-08-15
Have you tried browsing to your NAS via PLACES | NETWORK SERVERS, or connecting to it via PLACES | CONNECT TO SERVER yet?

What have you installed to get this to work? Anything yet? If nothing, follow the link I posted above. 

To answer your first question though: your music collection on the NAS will have to be mounted BEFORE any filesystem symlinks could be created, and if you have mounted it, there is no reason to create a symlink at all. Just mount it to the directory you want to.

What I would do:

sudo apt-get install smbfssudo chmod u+s /usr/bin/smbmnt

sudo chmod u+s /usr/bin/smbmnt

smbmount //myserver/myshare /home/yourusrname/MyMusic

[SIZE=3][/SIZE][SIZE=3]Where the //myserver/myshare 

is the IP & path to the stuff you wanted to originally "symlink" 
but in actuality is what you want to mount.


[/SIZE]

---

### Post by Redeyes_Gambit on 2006-08-15
Lol o gosh I can  believe I was so stupid! I hadn't installed smbfs :P Hence the problems. 

Thank you! all working now :)

---

### Post by fluffnik on 2006-08-15
No SMB here, but I can help with 3.

What windows calls shortcuts *nix calls links and there ar two ways to make them in Nautilus:

[LIST=1]
[*]Right click and choose "Make Link" which will make a new icon called "link to ..." which you can move to where you want

[*]Drag the icon to your chosen destination using the *middle* button and choose "Link" from the menu that appears whun you release the button
[/LIST]

You can also use the "ln" command from a terminal.

---

