---
title: "Rsync Will Not Stop Asking for Password"
date: 2009-05-11
forum: General Help
---

### Post by dr_latino999 on 2009-05-11
**NEW ISSUE**
[Client Freezes, Server receives folders but no files. This and more, on page 3!](http://ubuntuforums.org/showthread.php?t=1155604&page=3)



**OLD ISSUE**
I've been trying for about 6 hours now to get an rsync command to backup Windows files to Ubuntu without requesting a password. I tried the [ --password-file= ] command as shown in [http://justinsomnia.org/2007/02/how-to-regularly-backup-windows-xp-to-ubuntu-using-rsync/](http://justinsomnia.org/2007/02/how-to-regularly-backup-windows-xp-to-ubuntu-using-rsync/), but that did not work, as it was throwing a lot of Code 5 errors.

I then tried the shared ssh key, where as I requested the SSH key through the Windows setup and then followed these instructions to send it to Ubuntu as shown here - [http://optics.ph.unimelb.edu.au/help/rsync/rsync_pc1.html](http://optics.ph.unimelb.edu.au/help/rsync/rsync_pc1.html), no dice. Rsync still requests a password after the following command: ** rsync -e ssh -avz "/cygdrive/c/Documents and Settings/Edwin/My Documents/Test" edwin@192.168.1.115:edwinbackup **. If I enter the password at the prompt, the sync goes as planned but that defeats the purpose.

Any insight to what I am doing wrong here would be greatly appreciated, as I'm very new to the command prompt in a non-Windows environment. The ultimate goal is to figure out a command set that works so I may create a .bat file in Windows to backup automatically on a regularly scheduled basis.

Possibly Relevent - Rsync and associated commands in Windows environment running under Cygwin.

---

### Post by dr_latino999 on 2009-05-11
After 3 more hours looking at this problem I am no further along, I have to be missing something completely simple.

---

### Post by Peter09 on 2009-05-11
Best to get the password file problem resolved - I know this sounds silly but sometimes switching back to a known fault can resolve an intractable problem.

What command are you issuing when you try the password file?

---

### Post by Peter09 on 2009-05-11
I am not sure how relevant this is but code 5 suggests:

[QUOTE]
[/QUOTCOMPARE_FALSE. Used with the --r or --useCompareCodeResult option, an exit code of 5 indicates a given clear-text password does not match the provided encoded password.E]

---

### Post by jeromedavies on 2009-05-11
Are you sure you created the ssh key with a blank passphrase?

---

### Post by dr_latino999 on 2009-05-11
> **Peter09 said:**
> Best to get the password file problem resolved - I know this sounds silly but sometimes switching back to a known fault can resolve an intractable problem.

What command are you issuing when you try the password file?

The command I am trying is
> **rsync -qrtz --password-file=c:\cygwin\secret --delete "/cygdrive/c/Documents and Settings/Edwin/My Documents/Test" edwin@192.168.1.115::edwinbackup**The response I receive is 
> [B]@ERROR: chroot failed 
rsync error: error start client-server protocol (code 5) at /home/lapo/packaging/rsync-3.0.4-1/sr/rsync-3.0.4-1/src/rsync-3/0/4main.c(1504) [sender=3.0.4]
[/B]The relavent configurations files:

[quote=Ubuntu, rsyncd.conf][B]
[edwinbackup]
path = /home/edwin/backup
comment = Backup
uid = edwin
gid = edwin
read only = false
auth users = edwin
secrets file = /etc/rsyncd.secrets[/B]
[/quote]

[quote=Ubuntu,rsynced.secrets][B]
edwin:4073758256Cell
[/B][/quote]

[quote=Windows + Cygwin, c:\cygwin\secret][B]
4073758256Cell
[/B][/quote]

[quote=User Names]
Ubuntu = edwin
Windows = Edwin
[/quote]

[quote=jeromedavies]         Are you sure you created the ssh key with a blank passphrase?[/quote] I'm pretty sure, on the Windows+Cygwin side I did the following:

[quote=Windows Commands][B]
ssh-keygen -P ""
identity
[/B][/quote]

From this point I don't know how to do a command line transfer to Ubuntu from the Cygwin terminal to confirm I am setting up the ssh key properly on the Ubuntu system. I tried the **copy** command as found here: [http://optics.ph.unimelb.edu.au/help/rsync/rsync_pc1.html](http://optics.ph.unimelb.edu.au/help/rsync/rsync_pc1.html) but Cygwin responds with **bash: copy: command not found**.

---

### Post by Peter09 on 2009-05-11
In your rsync command the path to the file appears to reside on a c: drive, is that correct?

---

### Post by dr_latino999 on 2009-05-11
> **Peter09 said:**
> In your rsync command the path to the file appears to reside on a c: drive, is that correct?
Correct, Cygwin saved the password file (which was created in Cygwin) to it's default installation directory of C:\cygwin .

---

### Post by Peter09 on 2009-05-11
So you are unable to do a simple copy either - is that right.

Can you do this with a password?

---

### Post by dr_latino999 on 2009-05-11
> **Peter09 said:**
> So you are unable to do a simple copy either - is that right.

Can you do this with a password?
 
I believe the copy error lies within a package not being installed properly in Cygwin. I tried some different variations of rsync to see what would work and have saved the results as the following:
[IMG]http://farm4.static.flickr.com/3580/3522220108_548d29dbbd_o.jpg[/IMG]
[IMG]http://www.flickr.com/photos/12521531@N05/3522220108/sizes/o/[/IMG]

---

### Post by Peter09 on 2009-05-11
Note in the second attempt down the error for could not find the password file shows a different filepath to that specified. This is may be because \ has a different meaning in Linux - try putting the file name in quotes.

---

### Post by dr_latino999 on 2009-05-11
I modified the second one with quotation marks:

[IMG]http://farm4.static.flickr.com/3375/3521450221_4fc2563be9_o.jpg[/IMG]

---

### Post by Peter09 on 2009-05-11
try removing c: - shot in the dark on that one.

---

### Post by dr_latino999 on 2009-05-11
I removed c: and tried with and without quotation marks -

[IMG]http://farm4.static.flickr.com/3611/3521520183_fea26fc5c1_o.jpg[/IMG]

Same error for the one with "" and the one without, :confused:

Thanks for your help so far, going about this on my own was extremely frustrating.

---

### Post by Peter09 on 2009-05-11
Try removing the "

---

### Post by dr_latino999 on 2009-05-11
> **Peter09 said:**
> Try removing the "
 
No change from the prior command when removing the "

---

### Post by Peter09 on 2009-05-11
running short of ideas here - can you actually open the file, given the path that you are using?

---

### Post by dr_latino999 on 2009-05-11
Through Windows, no because there is no extension. In the shell I can using the command **vi /secret**, I'm free to open up the file and change the contents at will.

---

### Post by Peter09 on 2009-05-11
Will it do that with /cygwin/secret

---

### Post by dr_latino999 on 2009-05-11
**vi /cygwin/secret** opens a new directory that is empty.

---

### Post by Peter09 on 2009-05-11
:confused:

---

### Post by dr_latino999 on 2009-05-11
> **Peter09 said:**
> :confused: Let's backtrack then, at what point did my sleep-deprived brain wander off and stopped being helpful?

---

### Post by Peter09 on 2009-05-11
Sorry may be we are crossed here, it appears that the path within the shell is wrong, is that an issue?

---

### Post by dr_latino999 on 2009-05-11
> **Peter09 said:**
> Sorry may be we are crossed here, it appears that the path within the shell is wrong, is that an issue?

No need for apology, I really am quite prone to error right now; the error stems from the password file not being readable by Rsync. All the writeups I have found, on this forum and through Google have not mentioned any large errors with referencing a --password-file with the directory c:\cygwin\secret. This has caused all the confusion and deep personal loathing for the command line.

---

### Post by Peter09 on 2009-05-11
This may be your darkest hour  :) - however is there any light on a resolution yet?

---

### Post by dr_latino999 on 2009-05-11
> **Peter09 said:**
> This may be your darkest hour  :) - however is there any light on a resolution yet?

Not even a candle, I tried using the Windows program [DeltaCopy](http://www.aboutmyip.com/AboutMyXApp/DeltaCopy.jsp) to do the backup through a GUI and my favorite error appeared:

> Executing: rsync.exe  -v -rlt -z --delete "/cygdrive/C/Documents and Settings/Edwin/My Documents/MAE 442/Floor Beam.SLDPRT" "edwin@192.168.1.115::edwinbackup/MAE 442/Floor Beam.SLDPRT"
Profile 'edwin' executed in 0 milliseconds. It ran successfully.
@ERROR: chroot failed
rsync error: error starting client-server protocol (code 5) at /home/lapo/packaging/rsync-3.0.4-1/src/rsync-3.0.4/main.c(1504) [sender=3.0.4]

Error starting client-server protocol
Profile 'edwin' executed in 25906 milliseconds. One or more errors were encountered.
](*,)

---

### Post by dr_latino999 on 2009-05-13
After another day of trying a work around, I'm seriously confused. I have two variables: Server settings and Cygwin settings. I'm leaning more to an issue with Ubuntu as I tried the same rsync setup on my laptop and it failed with the same error.

---

### Post by dr_latino999 on 2009-05-20
I have gotten around Rsync asking for a password, by reinstalling Ubuntu on the server and Cygwin on Windows I was able to successfully log-in using a public SSH key. But here comes a new problem:


[quote=Rsync Command]
rsync -a --progress "/cygdrive/c/Documents and Settings/Edwin/My Documents/My Pictures" edwin@192.168.1.11: Pictures
[/quote]

I'm entering this command into the client (Windows) and I receive the following output:

[IMG]http://farm4.static.flickr.com/3546/3548291847_d730189c84_o.jpg[/IMG]

It looks good, but all it has done is freeze waiting for something - I don't know what - and it does nothing on the server side.

[IMG]http://farm4.static.flickr.com/3375/3548296493_35a4d5f6cb_o.jpg[/IMG]

Now if I change commands to

[quote=Rsync Command]rsync -arvW --progress --chmod u+rwx -e "ssh -i c:\cygwin\home\Edwin\.ssh\id_rsa" "/cygdrive/c/Documents and Settings/Edwin/My Documents/My Pictures" edwin@192.168.1.115: Pictures[/quote]

Once again the client freezes:

[IMG]http://farm3.static.flickr.com/2484/3548303193_0949cb83ba_o.jpg[/IMG]

But this time a folder structure is created on the Server but no files reside within the folders.

[IMG]http://farm4.static.flickr.com/3090/3548306897_713bfc47f9_o.jpg[/IMG]


Ideas / Suggestions / Creative solutions to get rsync to not freeze the client and / or transfer the files within the folders?


**EDIT**
It took 25 minutes, but one file has transferred. Is the server CPU usage supposed to be at 100%?

[img]http://farm3.static.flickr.com/2452/3549177222_fef0d62750_b.jpg[/img][IMG]file:///C:/DOCUME%7E1/Edwin/LOCALS%7E1/Temp/moz-screenshot.jpg[/IMG][IMG]file:///C:/DOCUME%7E1/Edwin/LOCALS%7E1/Temp/moz-screenshot-1.jpg[/IMG]

---

