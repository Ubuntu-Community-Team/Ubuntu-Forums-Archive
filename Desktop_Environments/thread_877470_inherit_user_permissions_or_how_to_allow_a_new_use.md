---
title: "inherit user permissions? or how to allow a new user to use other one files?"
date: 2008-08-01
forum: Desktop Environments
---

### Post by Bodhidharmazen on 2008-08-01
Hi

I have a problem with my account and I cant reach the desktop. After a few attempts I managed to create a second account and now I can access the computer, but, I have no longer access to my files.

Is there a way to inherit the access to such files? I am the only user of this computer and so I would like also to erase my first user. If I simply delete the user would I lost my files?

I copied all my files from the original folder to the new user folder (using the root account) but when I log in all the files are locked. I also entered the "user and groups" program and have put my new user in the original user group, no effect.

What can I do? I have a business trip next week and I need my files! :(

thanks

---

### Post by undecidable on 2008-08-01
I am not sure where your files are, but let me assume
you keep them in your home folder, so we are talking about:
 /home/olduser/documents
 /home/olduser/music
etc.
I also assume you are using Ubuntu not Kubuntu.
You have also said both olduser and newuser are in the same group.

1.  You need to:
a.  make sure you can see all the old files
b.  change the owner to newuser
c.  move them to your new home folder, so they will be in:
    /home/newuser/documents
    /home/newuser/music 
    etc.

2.  To make sure you can see the old files/folders:
open a terminal
(you will see 'terminal' on the menu, or alt-f2 then: "gnome-terminal")
and do:
```
  sudo chmod -Rv g+r /home/olduser
```
This will give the new user the right to look at the old files,
and show what is doing so you can check if it works.


3.  to change the owner, open a terminal again:
and do:
```
  sudo chown -vR newuser:  /home/newuser/documents
  sudo chown -vR newuser:  /home/newuser/music
```
this will change the owner of your old files to "newuser",
will keep the group the same,
and will list out what it is doing so you can see.

4.  To copy them across, the clearest way is to open two file browser windows 
(on your menu, or : alt-f2 then "nautilus").
Open one window to /home/olduser.
Open the other to /home/newuser.  
Then just drag and drop them across. 

If for some reason you want to do it in the terminal
you can do:
```
  cp -vR /home/olduser/documents /home/newuser/documents 
  cp -vR /home/olduser/documents /home/newuser/music
```

5.  Note that I suggest copying across your documents, music folders etc,
rather than copying across you whole old home directory.
The reason is that if you can't log-on, then there is likely to be some hidden file
in your old home directory that is corrupt. 
So best not to copy across the hidden files.

Hope this helps.

---

### Post by Bodhidharmazen on 2008-08-01
> **undecidable said:**
> I am not sure where your files are, but let me assume
you keep them in your home folder, so we are talking about:
 /home/olduser/documents
 /home/olduser/music
etc.
I also assume you are using Ubuntu not Kubuntu.
You have also said both olduser and newuser are in the same group.

1.  You need to:
a.  make sure you can see all the old files



thanks for this, I could not see some of the files, even when I know they are there some of the folders appear to be empty. So, before trying that thing about changuing its user I have to resolve this... I guess it is because of the groups? Hmm no, it can't be because both are in the same group (the original's user name). Also, using the administrator's "user and groups" I can see both users and enter their configuration options.

---

### Post by undecidable on 2008-08-02
It may be that you are looking in the wrong place.
I am guessing that you are clicking the places menu,
then clicking the Home folder.

BUT, this is the home folder for the new user.
You need to look in the home folder for the old user.
The olduser folder will be where your files are.
You need to find this and then follow the steps above.

Method 1
So click places, then filesystem, then home, and you should see two folders there:
[I]/home/olduser
/home/newuser[/I]

Method 2
Open accessories/file browser
(or alt-f2 "nautilus")
make sure view/location bar is checked
then type at the top in the location bar:
```
/home
```
this should show you the two folders there:
[I]/home/olduser
/home/newuser[/I]

Method 3
In alt-f2 type
```
nautilus /home
```
this should show you your two user folders.

**BUT NOTE:**
If you have found the /home/olduser folder,
and you still cannot see the files, 
then you need to follow step 2 below.
Just because you are in the same group,
it doesn't mean you can see the other user's files. 
The permissions may be rwx------
which means only the owner can see them!


Hope this helps.

---

