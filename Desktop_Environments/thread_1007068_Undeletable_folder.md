---
title: "Undeletable folder"
date: 2008-12-10
forum: Desktop Environments
---

### Post by GeorgeMurango on 2008-12-10
Hi all. I've spent weeks trying to rid myself of a folder. I recently converted a friend to Ubuntu after her vista laptop crapped out on her. She used my hard drive so save some of her documents. But one folder of them must have been encrypted or locked or something, because I can' delete it. It just sits in my recycle bin, mocking me. I try the 'delete permanently option, it says permission denied. I try to alter permissions, nothing. I've tried restoring it and deleting it again, still nothing. It's even resisted an entire system reinstall. (I saved all my data on the aforementioned hard drive to do a clean Ibex install)
Can anyone help me?

---

### Post by bibleman on 2008-12-10
Did you completely erase the hard drive using Boot and Nuke or similar software? 

I have seen this happen before but it was on a Windows box. After we used boot and nuke the file was gone though.

Your other shot is to be root and check permissions on it. It could be that it has some crazy permissions that is not allowing deletion.

---

### Post by sayakb on 2008-12-10
Try deleting it from terminal:
```
sudo rm /media/path/to/file
```
Careful with the command. This erases the file in a way that it is irreversible.

---

### Post by jman6495 on 2008-12-10
It May Belong To Another Account.
You Can Delete The File From Root SO Carefull With The Following

1. Press ALT and F2 At The Same Time.
2. In The Box Type "sudo nautilus" (Without The "")
3.Press Enter
4.You Are In A Root File Browser
5.Find The File
6.Try TO Delete It
-------------------IF THIS DOES NOT WORK---------------------------
7.It It Wont, Right Click And Go To Properties
8.Go To Permissions And Allow "Others" Read And Write Access
9.Close The WIndow And Try Deleting It Normaly

Hope This Helps
Jman6495
"Vista On 512MB OF Ram...A Tortoise Pulling A Mini"

---

### Post by sweetandy on 2008-12-10
> **LinuxIsInnovation said:**
> Try deleting it from terminal:
```
sudo rm /media/path/to/file
```
Careful with the command. This erases the file in a way that it is irreversible.

I think you mean rmdir; rm wouldn't do that unless you used -R to delete all contents of the folder recursively as well as the folder itself.

---

### Post by Leviathan88 on 2008-12-10
> **jman6495 said:**
> It May Belong To Another Account.
You Can Delete The File From Root SO Carefull With The Following

1. Press ALT and F2 At The Same Time.
2. In The Box Type "sudo nautilus" (Without The "")
3.Press Enter
4.You Are In A Root File Browser
5.Find The File
6.Try TO Delete It
-------------------IF THIS DOES NOT WORK---------------------------
7.It It Wont, Right Click And Go To Properties
8.Go To Permissions And Allow "Others" Read And Write Access
9.Close The WIndow And Try Deleting It Normaly

Hope This Helps
Jman6495
"Vista On 512MB OF Ram...A Tortoise Pulling A Mini"

Easier would be to use the terminal for this.  
 
sudo chmod 666 /media/path/to/file
or
sudo chown yourusername:yourusername /media/path/to/file

After either one of those commands!

$ rm /media/path/to/file ($ = as regular user)
or
$ rm -R /media/path/to/file  ($ = as regular user)

In any case use the -R flag to recurse into files and folders.

---

### Post by jenkinbr on 2008-12-10
> **jman6495 said:**
> It May Belong To Another Account.
You Can Delete The File From Root SO Carefull With The Following

1. Press ALT and F2 At The Same Time.
2. In The Box Type "sudo nautilus" (Without The "")
3.Press Enter
4.You Are In A Root File Browser
5.Find The File
6.Try TO Delete It
-------------------IF THIS DOES NOT WORK---------------------------
7.It It Wont, Right Click And Go To Properties
8.Go To Permissions And Allow "Others" Read And Write Access
9.Close The WIndow And Try Deleting It Normaly

Hope This Helps
Jman6495
"Vista On 512MB OF Ram...A Tortoise Pulling A Mini"
#2 should read:
2. In The Box Type "[highlight]gksudo[/highlight] nautilus" (Without The "")

Reason: sudo is a command-line implementation, whereas gksudo is graphical.  It would work fine from a command-line the way you had it, but when started from the run dialoge in that manner, it may not work.

@OP: where is the file/directory stored at?

---

### Post by GeorgeMurango on 2008-12-10
It's in the trash bin, and while I managed to get rid of the copies that had been made when I tried tp restore it and delete it again with the above methods, the original in the trash can't be restored or removed so far.

---

### Post by fjf on 2008-12-10
In a terminal, type:
> gksudo nautilus and you'll get nautilus with administrator rights.  Delete anything you want.

---

### Post by GeorgeMurango on 2008-12-10
For some reason root nautilus is unable to open the trash bin. It says the operation is not supported.

---

### Post by utnubuuser on 2008-12-10
Have you tried using > sudo su  ...then...
sudo rm -Rf /media/path/to/file

I'm not 100% sure on this, but if I'm not mistaken, the f adds =force

...and does the file have a special name, like /-nameoffile?  Because in that case you have to use rm -- -foo, or rm ./foo   and if it's got root status (/) it's something like rm --no-preserve-root

---

### Post by GeorgeMurango on 2008-12-10
> **utnubuuser said:**
> Have you tried using 

I'm not 100% sure on this, but if I'm not mistaken, the f adds =force

...and does the file have a special name, like /-nameoffile?  Because in that case you have to use rm -- -foo, or rm ./foo   and if it's got root status (/) it's something like rm --no-preserve-root

Just tried the above. When I hit enter in the terminal, it showed this  >
Just the arrow, and the file remained in the trash bin

---

### Post by Barriehie on 2008-12-10
I just had a similar situation happen to me this AM.  I ended up logging in as root and identifying my ***barrie*** trash bin as being the folder /.Trash-1000  This folder has 2 folders in it; one is files and the other is info.  I then entered a terminal and manually chmods to 777 everything in the files subfolder and proceeded to rm everything.  This worked and took about 45 minutes...  Might be a more elegant solution but at this point my trash bin is empty!  I'm using Hardy 8.04 if it makes a difference.

Barrie

---

### Post by RJARRRPCGP on 2008-12-15
> **GeorgeMurango said:**
> Hi all. I've spent weeks trying to rid myself of a folder. I recently converted a friend to Ubuntu after her vista laptop crapped out on her. She used my hard drive so save some of her documents. But one folder of them must have been encrypted or locked or something, because I can' delete it. It just sits in my recycle bin, mocking me. I try the 'delete permanently option, it says permission denied. I try to alter permissions, nothing. I've tried restoring it and deleting it again, still nothing. It's even resisted an entire system reinstall. (I saved all my data on the aforementioned hard drive to do a clean Ibex install)
Can anyone help me?

Your problem of access being denied when emptying the trash reminds me of an old bug from Windows 98. Windows 98 has a bug where it will bring a file to the recycle bin, but won't let you empty it. LOL. 

Unfortunately, sounds like you need to DBAN it!

---

### Post by AlexOslo on 2008-12-19
> **GeorgeMurango said:**
> For some reason root nautilus is unable to open the trash bin. It says the operation is not supported.

I noticed that too, but I just went into the trash folder from another window and could delete it using the button at top right (Ubuntu 8.04).

---

### Post by AlexOslo on 2008-12-19
> **fjf said:**
> In a terminal, type:
 and you'll get nautilus with administrator rights.  Delete anything you want.
Worked very well for me (Alt+F2, then gksudo nautilus + enter, that is)--I could delete locked files I was unable to delete otherwise!

---

### Post by wankel786 on 2008-12-19
> **AlexOslo said:**
> I noticed that too, but I just went into the trash folder from another window and could delete it using the button at top right (Ubuntu 8.04).

try: gksudo dbus-launch nautilus
this will let you into the trash folder.

---

