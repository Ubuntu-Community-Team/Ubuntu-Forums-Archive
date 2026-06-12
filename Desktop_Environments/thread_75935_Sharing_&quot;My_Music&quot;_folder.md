---
title: "Sharing &quot;My Music&quot; folder"
date: 2005-10-14
forum: Desktop Environments
---

### Post by mojogil on 2005-10-14
Hello,
  I'm a new linux user and have tried Suse, Mandrake, and now Ubuntu.  I think I'll settle in with Ubuntu as it is simple and does everything I need it to do.  
My kids and I share a computer and we are all logging in with our own screen names.   
My hard drive is only 40 gig and my music folder is almost 20 gigs.  I'm trying to set the permissions on the folder so everyone can access it and play the music but it looks like I'll have to go to every single song and set the permission.  Is there a simpler and faster way to do this?
Thank you!
Gil

---

### Post by olsen on 2005-10-14
Yes. The R argument should do this for you.

f.ex:

chmod 775 Music -R

---

### Post by HermanAB on 2005-10-14
Much better solution - stream the music from your PC using Edna, an ultra simple streamer.  

See the end of this guide:
[http://www.aerospacesoftware.com/ogg2mp3-howto.html](http://www.aerospacesoftware.com/ogg2mp3-howto.html)

Works like a charm!

Cheers,

Herman
[http://www.aerospacesoftware.com/linuxhowtos.html](http://www.aerospacesoftware.com/linuxhowtos.html)

---

### Post by wylfing on 2005-10-14
Some additional explanation might be in order. The -R switch means "do this operation recursively for all files and directores under this one." The 775 part (which I don't think is quite right) changes the priveleges to allow anyone to read the music files, but restricts writing to only the owner and the members of the appropriate group.

Now that last bit is the key to how to do this kind of thing properly in a Unix-like environment. What you really should do is set up a "music" group and allow members of that group to access the tunes.

1. From the main toolbar, choose System > Administration > Users and Groups. 

2. Click the Group tab.

3. Click Add Group and type [FONT="Courier New"][COLOR="DimGray"]music[/COLOR][/FONT] in the Group name box.

4. Use the two Group Members listboxes to add users to the new group (presumably, you and the kids). When you're satisfied, click OK.

5. Open a terminal and navigate to one directory level above your music folder (i.e., so that if you type [FONT="Courier New"][COLOR="DimGray"]ls -d[/COLOR][/FONT] you will see its name in the list).

6. Run these two commands:
```
chgrp music foldername -R
chmod 770 foldername -R
```

Where "foldername" is the name of the music folder you want to share. (If there are spaces in the name, put double quotes around the folder's name.) These commands will set the permissions of all the files so that you (the owner) can do anything with the files and everyone in the music group will also be able to do everything with the files. But no one else will be able to even look at them.

It could be that there is some music you'd rather not share with the kids. In that case, just use Nautilus to change the group of those files:

1. Open a Nautilus window and navigate to the music you don't want to share with the kids. Right-click the folder and choose Properties.

2. Click the Permissions tab. There is a pop-up selector called File Group. Use it to set the group to the same as your user name, and make sure none of the checkboxes under Other are selected. Click OK.

That way, nobody but you will have access to those particular files.

Lastly, you may want to make a link to this shared music folder and put it into the kids' home directories. Using Nautilus, right-click the shared music folder and choose Make Link. Then copy and paste that into their homes. That way they can jump straight into the music folder, where they'll have access to everything that's part of the music group.

---

### Post by mojogil on 2005-10-14
Thank you Wylfing!
  As I said, I'm pretty new at this.  I'm not sure how to navigate to files and folders in the terminal.  I can open the terminal I just don't know what to type. I just picked up "Linux For Dummies" and will be reading it while camping this weekend, hopefully that will get me up to speed.  It comes with Fedora Core but I'm just going to apply what I can toward Ubuntu since it runs so smooth and quick on my fairly old computer.
Take care,
Gil

---

### Post by Curlydave on 2005-10-14
Here's what I do: I have a 5gig fat32 partition that Linux and Windows can both easily read/write. I have my Documents in a folder in it called "Documents", and my music in a folder called "Music". I use this folder for both windows and linux. Easy enough.

---

### Post by mojogil on 2005-10-14
Curlydave,
  That's a great idea and simple!  I'll probably do that.  I still want to learn how to do the folder setting though.
Thanks!
Gil

---

### Post by wylfing on 2005-10-16
It's not essential to do the part with the command-line terminal. It's just *waaaay* faster to do it that way. See the last few steps, where I talked about setting permissions by right-clicking stuff and choosing Properties? Just use that method to set the permissions on whatever you want.

Put in context: Right-click a music file (or a drag-select a bunch of music files), right-click, and choose Properties. Click the Permissions tab. Use the File Group selector to change the group to "music" (assuming you've created that group already), and then select or deselect the checkboxes to fine-tune who can get access to the files.

---

