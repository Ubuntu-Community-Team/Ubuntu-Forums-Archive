---
title: "Windows Share: Opens PDF Won't Open OO Files"
date: 2006-08-29
forum: Desktop Environments
---

### Post by wacole on 2006-08-29
I am running 5.10.  I have a Windows share mounted as an icon on my desktop.  I can connect to the share through Nautilus and see all the files.  I can open a PDF file [go figure] from that share but I can't open anything else, which mostly includes OpenOffice files of various sorts.  Can't open any sort of image file [png, jpeg, etc.] either.

I read and tried the suggestions in the thread "_Trouble opening Images and Mp3s from a Windows Share_" but on start-up the "Mounting local file systems ..." "failed" because it could not find the share.  I think I have it properly defined in the fstab, but I could be wrong. [BTW I commented that share line out in the fstab and re-started, this time w/o complaint from the booter.]  Oh, and even w/o the fstab entry I can still connect to the share but still can't open most of the files.

Is this a rights problem, please.  I'm just stumped.

Thanks for any clues that would be offered.

Bill Cole

---

### Post by huygens on 2006-08-29
I am not sure what is your problem...
But let's try something (I assume you have Windows XP), open a terminal (Applications, then Accessories, then Terminal) and type:
```
smbclient -L *host* -U "*host\user*"
``` Replace 'host' by the hostname of your windows box, and replace 'user' by a windows username which has access to the share drive. So for example, if your Windows computer is called win and you log in using the account huygens, then the command line should be like:
```
smbclient -L win -U "win\huygens"
``` It might prompt you for a password, enter your windows password.
It should display some information on the SMB network and the list of shares available on the windows host. Much like this:
```
[FONT=Courier New][SIZE=2]Domain=[WORKGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        **Share**           Disk
Domain=[WORKGROUP] OS=[Windows 5.1] Server=[Windows 2000 LAN Manager]

        Server               Comment
        ---------            -------
        WIN                 My windows XP box

        Workgroup            Master
        ---------            -------
        WORKGROUP            WIN[/SIZE][/FONT]
``` Let's assume that one of the shared folder displayed in the list returned by the previous command is called "Share".
```
smbclient "//win/Share" -U "win\huygens"
``` By this you connect to the SMB shared folder much like you would to a FTP server in a command line. You then get a display like this:
```
smb: \> 
``` Type 'ls' (without the single quote) for example, this will list the files you have. You need to type 'cd' to change of directory (to change to directory document, you type 'cd document', always without the single quote). Now if you see one of this file that you cannot open (for example I assume that you have doc.odt and you cannot open it). Try the following command:
```
get doc.odt
``` You should see the transfer of the file:
```
getting file \doc.odt of size 40160 as doc.odt (4902.3 kb/s) (average 4902.3 kb/s)
```If you have a problem there, could you post the output of the command?
Open Nautilus (your file manager, it is in the "Places" menu, choose "Home Folder"), and see if the file you just downloaded is readable.

Huygens

---

### Post by wacole on 2006-08-29
Thanks very much for those instructions which worked perfectly.

I thought that the problem is that the file names on my W2K share contain spaces.  For example if I do a get on 'file name.odt' [I did it both with and without the single quote and got the same result] the message NT_STATUS_OBJECT_NAME_NOT_FOUND ... is returned.  So I went to W2K Explorer and renamed the file by replacing spaces with underscores, to 'file_name.odt' and ran get [this time omitting the single quotes] and get worked just fine, meaning that it returned "getting file ... etc."

However, when I go to Nautilus and double-click on the file that I just renamed - the one where I replaced spaces with underscores - I get:

*Couldn't display "smb://192.168.1.106/wcole/My...23_process_paper_template.odt".*

message.  Interestingly, several of the PDFs in the share that I connect to have file names that have spaces and they open just fine from Nautilus. [I'm using the Adobe 7 Reader for Linux].

Thanks again ...

---

### Post by wacole on 2006-08-29
Additional information - all files are on a Windows share:

Opened by double clicking on Nautilus file name:
.html files open fine w/Firefox
.txt files open fine w/gedit
.bmp file will start Gimp but yields 'no such file or directory'
.jpg file will start Gimp but yields 'no such file or directory'
.tiff file will start Gimp but yields 'no such file or directory'
.gif file will start Gimp but 'image loading failed ... unrecognized image file format' (though the thumbnails display just fine ... clicking on the thumbnails yields same result)
.png file will start Gimp but 'image loading failed ... unrecognized image file format' (though the thumbnails display just fine ... clicking on the thumbnails yields same result)
.pdf files open fine w/Adobe Reader 7
.xls files open sort-of fine w/Gnumeric

Opened by right clicking on Nautilus file name, selecting 'Open with other application' and selecting an appropriate application from the drop-down list:
.doc files open w/OO Write but the file name is "Untitled1" and is empty
.odt same
.sxw same
.rft same
.wpd same (OO2 will open native .wpd files)
.ods files open w/OO Calc but the file name is "Untitled1" and is empty
.sxc same
.sxd files open w/OO Draw but the file name is "Untitled1" and is empty
.ppt file open fine w/OO Impress

---

### Post by huygens on 2006-08-30
Hello,

For the problem with the space in the filename, you could use the double quote to circumvent it.

As for your problems. I have tried to open PNG file with the Gimp on my share drive. The Gimp does not recognise the smb://... path to your file. Thus, it prepends your home directory before, resulting in something like: /home/ubuntu/smb://...
This is of course not the correct path. So Gimp cannot handle this type of path.
It seems to be the same problem with Adobe Reader :-( it seems to allways start with a / the path to a file. Thus it cannot work. Notice that in my case, Adobe Reader opens but no file are displayed, nor any error/warning message! :confused:
Now with Open Office file, well it works good to open them, but I cannot save to the share directory :-(
So those figures are a bit different than yours and I cannot figure out why.

A solution to all of this would be to *mount* your share just as a local directory. To understand what I mean, this is just like creating a network drive under Windows (remember when you right click on a shared directory under Windows, you can choose "Map network drive", and then this share appears just like a partition on your computer). Well good news, you can do the same trick with Linux :-)
Here is what you need to do (I am using the same assumption as in my previous post, only the share folder name is now "Share Folder" so it contains a space)
```
sudo apt-get install smbfs
sudo mkdir /mnt/share
sudo mount -t smbfs //win/Share\ Folder /mnt/share -o username="win\huygens"

```It will request you a password. After this the SMB share folder is mapped to the directory /mnt/share. If you go exploring with Nautilus, you go to "File System" -> "mnt" -> "share" and then you can access and open all of your files.

What you need to know is that at next reboot, you will need to do the last of the three commands again.
What you could do is add a line in the file that manage partitions and disks (/etc/fstab).
So edit the file:```
gksudo gedit /etc/fstab
```Now add this line: ```
//win/Share\040Folder /mnt/share smbfs credentials=/etc/smb-pw/win 0 0
``` A bit of explanation, the spaces in the share drives have to be replace by '\040', and the login and password are going to be place in a file that is private to the super user (not readable by others). Here is how to do it:
```
cd /etc
sudo mkdir smb-pw
gksudo gedit smb-pw/win
sudo chmod 0600 smb-pw/win
sudo chmod 0700 smb-pw
``` OK this is the complete code, however, after executing the 3rd command, you will have the text editor opened. Here is what you have to put in, then you save and exit the editor and proceed with the rest of the above commands:
```
username=win\huygens
password=my_1ncredible_passwd
``` Of course replace the username and password by yours :-)
Now, at each boot you will have your windows share under /mnt/share.

Just to test it right now. First unmount your share if you have done it previously. And then mount it using fstab. Here is how to do it:
```
sudo umount /mnt/share
sudo mount /mnt/share
``` The first line will look in the mounted partition the /mnt/share mount point and unmount it (detach for the shared folder). The second line will look in the /etc/fstab file for a share that shall be mounted under /mnt/share.

OK, I hope it helps and solve your problem :-)

Huygens

---

### Post by wacole on 2006-08-30
Thanks very much, I really appreciate your thoughtful responses.  I'll give this a try tomorrow and report back.

---

### Post by wacole on 2006-09-01
Hello,

Thanks very much for the additional instructions.

Some assumptions:
Host Name: pippin
User Name: auser1
Share Name: auser2
Share Folder Name: Documents and Settings\auser3

I got the /mnt/share subdirectory made.  Then I went to mount the directory using:

*sudo mount -t smbfs //Pippin/Documents\ and\ Settings\auser3 /mnt/share -o username="pippin\auser1"*

Which returned:

[I]22382: session setup failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed[/I]

So I've done something wrong but not sure what, though I suspect it has to do with what I'm interpreting to the be the Share Folder.

Thanks very much,

Bill Cole

---

### Post by giambrone on 2007-04-12
What should I do if I don't need a username? Sorry for playing it silly!

---

### Post by huygens on 2007-04-12
> **wacole said:**
> Some assumptions:
Host Name: pippin
User Name: auser1
Share Name: auser2
Share Folder Name: Documents and Settings\auser3

I got the /mnt/share subdirectory made.  Then I went to mount the directory using:

*sudo mount -t smbfs //Pippin/Documents\ and\ Settings\auser3 /mnt/share -o username="pippin\auser"*

Yes the correct line should be:
```
sudo mount -t smbfs //pippin/auser2 /mnt/share -o username="pippin/auser1"
```But just to be sure, you should do:
```
smbclient -L pippin -U "pippin/auser1"
```If it does not work. Try to figure out your "workgroup" or "domain" you are using under Windows, and replace "pippin/auser1" by "workgroup/auser1" with workgroup being the name of your workgroup or domain.

To check for the workgroup/domain name of your computer under Windows: Control Panel -> System and a window will appear. Then you go to the "Computer Name" tab. there you will find an information about the domain name. If the domain is something of the form foo.company.com, then you can use just "foo" for the domain (workgroup) name.

---

### Post by huygens on 2007-04-12
> **giambrone said:**
> What should I do if I don't need a username? Sorry for playing it silly!
Good question. I assume, you still have to enter a password...
I will have to look through the Samba documentation and post back later. I have no idea at the moment.

---

