---
title: "password protect folder/files?"
date: 2005-04-11
forum: Desktop Environments
---

### Post by cmikepee on 2005-04-11
i'm relatively new to linux and i was wondering if there was a way to easily make a folder that can only be opened using a password.  I want to have a folder containing files that only i can have full access to while anyone else cannot access, even when logged in under my username.  so basically i want to be able to set a unique password for this folder, different from my login password.  What i am doing currently is setting the folder so only the root can have access to the folder and using sudo whenever i want to access the folder.  however, anyone who knows my login would also know my 'sudo' password.  It is also an extra step if i have to 'sudo konqueror' everytime i want to access the folder.  what would be really great would be if i could just click on the folder and have it prompt me for the password.  I'm not sure if this is some type of setting i could do or would it be more on the level of an external program?

---

### Post by nemin on 2005-04-11
[QUOTE=cmikepee]i'm relatively new to linux and i was wondering if there was a way to easily make a folder that can only be opened using a password.  I want to have a folder containing files that only i can have full access to while anyone else cannot access, even when logged in under my username.  so basically i want to be able to set a unique password for this folder, different from my login password.  What i am doing currently is setting the folder so only the root can have access to the folder and using sudo whenever i want to access the folder.  however, anyone who knows my login would also know my 'sudo' password.  It is also an extra step if i have to 'sudo konqueror' everytime i want to access the folder.  what would be really great would be if i could just click on the folder and have it prompt me for the password.  I'm not sure if this is some type of setting i could do or would it be more on the level of an external program?[/QUOTE]
Since the root-account has all possible rights, any protection would be worthless when someone knows the password from a user who can access sudo and gain root privillages this way. I think you should be more carefull with your user password ;)

---

### Post by cwaldbieser on 2005-04-12
I have to agree with nemin.  The easiest way to accomplish what it sounds like you want to do is to create a new user that does not have sudo privledges, and put files you want others to be able to access under that user.  If you want to access some of your sudoer user's files from that account, you can still su (switch user) to that account, because only you should know that user's password.

If other users are going to have sudo privledges, then the only way I can think of to do what you want is to encrypt the data in the folder somehow, and un-encrypt is when you want to access it.  Something like KFileCoder ([http://kfilecoder.sourceforge.net/)](http://kfilecoder.sourceforge.net/)).  Not sure what is in the repositories like this program, but I am sure some Googling could turn up some more alternatives.

---

### Post by nemin on 2005-04-12
[QUOTE=cwaldbieser]
If other users are going to have sudo privledges, then the only way I can think of to do what you want is to encrypt the data in the folder somehow, and un-encrypt is when you want to access it.  Something like KFileCoder ([http://kfilecoder.sourceforge.net/)](http://kfilecoder.sourceforge.net/)).  Not sure what is in the repositories like this program, but I am sure some Googling could turn up some more alternatives.[/QUOTE]
*REALLY* paranoid users wouldn't use this possibility either, since the root user could hack the de/encrypt program to findout the key;) 
For normal users, I think this could be a good option :)

---

### Post by maqi on 2005-04-12
You might want to remove the bracket from the end of that link :-P

*REALLY* paranoid users would lock their computer in a vault - unplugged. They would never turn it on with someone else in the room and when/if they did boot up they certainly wouldn't connect to a network or save any information on it  :twisted: 

Root could install a script which is called along with the encrypt/decrypt program and log the password keystrokes - much easier. The NSA could have forced Linus to insert trojan code into the kernel. My tin-foil hat might not work :shock:  8-[ (God, I hope the tin-foil hat thing isn't true) 

I don't take security lightly, but I mean come on folks :roll:

 :smile:  :smile:  :smile: 

maqi

P.S. to the original poster - If this is information that you want to protect very much then you should consider just how much - there is always a tradeoff between security and convenience. Think of it this way - more convenience=less security. So how bad do  you want to protect these folders?

---

### Post by maqi on 2005-04-12
cmikepee: There doesn't seem to be much on offer. Most encryption tools available for Linux use strong encryption and provide good security - so they're not as convenient as you're looking for.

One thing you could do if you don't mind a little inconvenience is install gnupg and kgpg. Gnupg is a very good command line encryption program. You can use it to encrypt or digitally sign files and emails with a key which you need to generate. Kgpg is a gui frontend for gnupg which makes using it much easier. 

The advantage of Kgpg over other gnupg front ends is that you can run it in your system tray and have it encrypt and decrypt files by simply dragging them onto the icon in the system tray. When you encrypt a file the encrypted version will appear in the same directory where the original file is or was. You can also have it shred (overwrite with gibberish) the original file which you encrypted. When you decrypt the new file will again appear in the original directory. When you drag a file for decryption you are asked for your passphrase. When you provide it the decrypted file automagically appears.

The encrypted file is not deleted. But if you make changes to a file or directory after decryption and keep the same name you can then drag it to the kgpg icon and it will ask you if you want to overwrite the original encrypted file with the new version. You just say yes and voila!

But:

NEGATIVES:
If you use it to encrypt a directory it will create a compressed archive of the directory and then encrypt it but you cannot automatically shred directories so you then need to delete the source directory yourself. In addition - when you decrypt the file you will end up with a compressed archive of the source file (zip, gzip or bip2) which you then have to uncompress before you can get at the original directory. So it is a little fiddly.

You should also understand that it is a wise idea to do some reading about PGP, GnuPG and security/cryptography to use this (or ANY encryption/security) application in a reasonably secure manner. So there's a bit of a learning curve involved if you want this level of security - but it's rather interesting :)

POSITIVES:
Good strong encryption. It doesn't matter who is logged onto your system - if they don't know the passphrase for your encrypting key (and if it's a strong passphrase) then not even root can get at the encrypted files - apart from deleting them. And root can do that whenever root wants. The drag and drop functionality of kgpg makes this one of the easiest ways to do this. Both gnupg and kgkp are available via synaptic from the ubuntu repositories.

So think about how important to you the contents of this folder are. And if this isn't too much trouble for you - and the learning curve is probably the hardest bit - give it a go.

Hope this helps

maqi

---

### Post by glorybe on 2008-06-06
I beleive many encryption programs can do what he asks. Why not simply encrypt the entire directory. There is no need to store the password anywhere on the computer. It does not matter who has root access as root will not have the password and all files in the directory will be encrypted.
          One way to keep the password on the computer yet make it useless to others is to use any encryption program that allows really long passwords and use something like the entire first sentence from Chapter 2 of a book that resides on the computer. Copy and paste the sentence when prompted for the password and all is well.
That is also a great way to have a complex password as the sentence in question might have numbers or even a street address within. Trying to crack that kind of password just won't yield any good results. I like to murder a nursery rhyme or jingle that sticks in the mind as a password. Even a catchy tune can do. "Love me tender. Love me true.Love me with Accent meat tenderizer." is the type of nonsense that would be really hard to crack.

---

### Post by robinc on 2008-06-07
chown :)

---

