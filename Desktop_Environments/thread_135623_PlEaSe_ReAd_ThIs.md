---
title: "PlEaSe ReAd ThIs"
date: 2006-02-24
forum: Desktop Environments
---

### Post by cornboyl on 2006-02-24
Help anyone is there a way to stop ubuntu from clearing files from /tmp coz thats where runescape downloads and when i reboot or turn on all the files are gone and i am using dial-up so its slow to redownload.
any hints to disable clearing files in /tmp

(the file of runescape is called .file_store_32, i tested it with other files and also go deleted)

---

### Post by yanik on 2006-02-24
You should see if you can change the dir where your game writes.  Your /tmp will fill your disk very fast.

---

### Post by cornboyl on 2006-02-24
Nope its impossible.
Runescape only uses 10-15megs anyway.
How come all debian linux's it always removes files on tmp and on RPM based like fedora, Mandriva/ake Asianux and all that dont remove?:confused: 

Please help me, my msn is [email]cornboyl@hotmail.com[/email]

---

### Post by brentoboy on 2006-03-07
I agree, this is the most anoying thing of all time. (well, maybe not, but it is pretty anoying)

If I download something zipped, and let it open up with file-roller.  Then close firefox.  the file gets deleted. (it seems the trigger for deleting a tmp file is closing the app that created it).

So, even though I have it opened, it is deleted. So, When I try to extract the file, it errors out becuase the file is gone now.

--

even more anoying is this situation,
Download a Doc file, open it with oowriter instead of saving it. close firefox now its in /tmp edit it. click save.  close oowriter.  Realize you saved your only copy in /tmp.  Try to reopen it 3 seconds later - too bad, its gone.

certainly there is a way to tell temp to wait a couple of hours before deleting files that are accumulating.  Somebody's got to know where this setting is stored...

I cant help but think that a more specific title on this would have generated more hits, and therefor more feedback.

---

### Post by nocturn on 2006-03-07
[QUOTE=brentoboy]
If I download something zipped, and let it open up with file-roller.  Then close firefox.  the file gets deleted. (it seems the trigger for deleting a tmp file is closing the app that created it).
.[/QUOTE]

That's not Ubuntu.  That is FireFox.  It is cleaning up it's temp files when closing...  It would do so too on an RPM system.

---

### Post by brentoboy on 2006-03-07
cornboyl,

Here is what I found at 

[http://www.debian-administration.org/articles/83](http://www.debian-administration.org/articles/83)

in the /etc/default/rcS
file, you can change TMPTIME to set the number of days before tmp files are automatically removed.

this might help your situation.
It looks like it controls the decision to delete at system reboot, not the constant removal we are seeing.
---
Nocturn,
that may be the case, I'd have to play around to be sure.  But, I dont think that that is the case for runescape if that is their default save location for new downloads.
So, I have to figure that ubuntu is cleaning house too.

---

### Post by Ocxic on 2006-03-07
/tmp is there as a temporary loaction for files thats why it's called /tmp you shouldn't be trying to save anything there. and i'd get runscape to download there files to a differnet directory, cause eventually /tmp will get cleard out.

---

### Post by taurus on 2006-03-07
If you download files, save them to your home directory, not /tmp unless you want them to get wiped out.  I always create a temp directory in my $HOME and save all the stuff there,
```

mkdir ~/temp

```

---

### Post by MichaelZ on 2006-03-07
Hello,

May be before re-booting, turn off/on, you can copy the files to your /home directory and re-copy them to the /tmp directory after the re-booting or whatsoever is finished. May be a script could be used for doing this.

Best wishes,
Michael

---

### Post by brentoboy on 2006-03-07
so, I performed a "scientific" experiment.

I put a file in /tmp using cp ~/somefile  /tmp/somefile
to see when it got deleted.

I also added a file by openign gedit and saving some junk text into /tmp/sometext

then closed all the apps - just to see if closing the program that created the file had any affect.  - it doesnt.

both files are still in there.  It looks like I confirmed nocturn's idea that ubuntu is not deleting the files - firefox is.

And, if firefox is deleting my tmp files, then maybe runescape is deleting yours.  maybe it downloads to there, and then saves them where you ask it to, then deleting the files after it closes (or after it moves them elsewhere)

the only time ubuntu deletes files is when you reboot. - which can be avoided b editing the script file I mentioned above. (a few posts up)

I think that pretty much covers it.  I'd have to get runscape to be more helpful than that.

---

