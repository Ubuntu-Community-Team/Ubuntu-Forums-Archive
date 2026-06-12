---
title: "Rhythmbox ID3 tag issues"
date: 2005-12-18
forum: Desktop Environments
---

### Post by zoqaeski on 2005-12-18
G'day everyone

For some reason, nearly all of the music I import into the Rhythmbox library always has the tags messed up. Whenever I burn a CD or get music onto the computer, I always edit its tags with EasyTag to make sure its all right. But then I import the tracks into Rhythmbox, and they all get stuffed up; I dunno why.:mad: 

So far, the only way I can fix this is by opening the .xml file in /home/$user/.gnome2/rhythmbox/ and manually editing all of the fields, but this is tedious and still doesn't work sometimes. I've tired purging the library and starting again, but it just doesn't work.

Any ideas what the problem is?:???: 

cheers
Robbie

---

### Post by linuxguiri on 2006-03-21
From Rhythmbox FAQ:
[http://www.gnome.org/projects/rhythmbox/faq.html](http://www.gnome.org/projects/rhythmbox/faq.html)

 Why will preferences not let me edit my song tag info?

    Some mp3s are not detected properly by GStreamer. Rhythmbox supports id3 tag editing as an experimental feature. This is a feature that will be supported at some point in the future. Use the --enable-tag-writing flag to configure to enable it, at your own risk obviously.

So if I cannot edit my song tags in Rhythmbox, what is the best way?

    A 3rd party application like EasyTAG will allow you to edit your song information.

---

### Post by abbot on 2006-11-07
No man.  He already said that he edits his tags with EasyTAG but they still don't display properly in Rhythmbox.  I'm actually having the same problem with some of my files.

I edit all of my ID3 tags in EasyTAG, which usually works very well.  In fact I think it's the best ID3 editing program I've ever used for any OS.  For some of my albums however, it seems like there is hidden ID3 information that Rhythmbox displays rather than what I changed the tag too.  I can even pull the same files up in TagTool, KID3 or whatever other ID3 app. and they all display the correct information which I saved to the tracks using EasyTAG, even though Rhythmbox is still displaying this ghost info.  I have also used these different programs to completely remove all ID3 versions and re-write them, yet the ghost info is still there in Rhythmbox, so I know it's not a problem with EasyTAG.  I know that all my file permissions allow writing as well.

Now that Rhythmbox actually supports changing file properties out of the box it is possible to correct the display names inside of the program, which actually seems like it works.  That is until the next time you restart Rhythmbox and all the file info is back to how it was before.  On top of that, when I do edit files inside of Rhythmbox, then pull them up in an external ID3 app. they always display the files as having no ID3 info at all.  I know that this Rhythmbox feature is experimental, but this doesn't really effect the issue at hand anyway and is more of a seperate problem.

Is this ghost info a problem with Rhythmbox? or could it be the linux ID3 libraries themselves.  I'm really anal about ID3 tags so this problem is Super Annoying.

---

### Post by maubp on 2006-11-09
I think it might be down to the ID tag version.

I haven't double checked this, but I think RB and gstreamer support v2.4, while EasyTag does not.  

EasyTag will read and write ID3v2.3

It *might* be that your tracks now have two sets of tags...

---

### Post by abbot on 2006-11-09
are there any id3 editors that you know of that do support the newer ID3 version?  as i mentioned i have used various other programs with the same result.  TagTool, exfalso, KID3 are some that i remember using.

---

### Post by brcre on 2006-11-09
.

---

### Post by dpm on 2006-11-09
> **abbot said:**
> are there any id3 editors that you know of that do support the newer ID3 version?  as i mentioned i have used various other programs with the same result.  TagTool, exfalso, KID3 are some that i remember using.

Some background info, maybe it helps:

[http://www.ubuntuforums.org/showpost.php?p=1184248&postcount=16](http://www.ubuntuforums.org/showpost.php?p=1184248&postcount=16)

[http://www.ubuntuforums.org/showthread.php?t=287811](http://www.ubuntuforums.org/showthread.php?t=287811)

Cheers.

---

### Post by abbot on 2006-11-09
Hmmm.  So it looks like there may be ID3v2.4 tags attached to the files that I'm having problems with but I have no way of editing those tags because all the ID3 editing programs will only support up to ID3v2.3?  Until the tagging features in Rhythmbox work properly or EasyTAG's libraries are given v2.4 functionality I'm kinda stuck?

An example of the Rhythmbox ID3 editing problem I'm having is this.  I have multiple tracks by the same artist "Boxcutter" which is what some of the problem files are.  Some of the files are displayed as "Boxcutter" and some of the files are displayed as "boxcutter" the only difference being the capitalization of the artists name, but this none the less is registered as 2 separate artists in rhythmbox's browser.  I can change the case in the artist name properties for the track and it will stay uppercase for maybe 10 seconds before automatically reverting back to the lowercase spelling in the library list & browser.  Very odd.

---

### Post by aminaiee on 2006-12-12
Hi,

I have used eyeD3 for editing and upgrading ID3 tags to v2.4. Have a look at the following:

[http://eyed3.nicfit.net/]("http://eyed3.nicfit.net/")

Cheers,
Hossein Aminaiee

---

### Post by aysiu on 2006-12-12
TagTool makes a very clear distinction between v.1 and v.2 tags.

---

### Post by UlyssesR on 2007-02-05
Well, I have a dirty workaround for this.

First I converted all my files to ID3v2.4 with eyeD3 (sudo apt-get install eyed3):
```
find music-dir/ -iname "*.mp3" -exec eyeD3 --to-v2.4 {} \;
```

Then, I noticed that all files with mismatched tags ended with a TAG'whatever information here' string. I tried to use apetag to remove these, however it didn't work, so I made a dangerous script in python to truncate the mp3 file when it finds this TAG pattern in the end of the file (based on the code of rmid3v1.py from apetag tarball).

```

tag-wipe.py

#!/usr/bin/env python

# truncates a file after a TAG pattern is found
# use at your own risk!
#
# for a bunch of files, you may want to:
# find somewhere/ -iname "*.mp3" -exec tag-wipe.py {} \;
#
# ulysses - ulysses@naosei.net

import sys

def main ():
	name = sys.argv[1]
	input = file(name, "r+")

	offset = -1024
	input.seek(offset, 2)
	pos = input.tell()
	
	while (True):
		tag = input.read(3)
		if (tag == "TAG"):
			print(name + ": found the damn tag - truncating at 0x%08x") % pos
			input.truncate(pos)

			input.close()
			sys.exit()
		else:
			if (offset >= -2):
				print(name + ": no damn tag found")
				input.close()
				sys.exit()
			else:
				offset += 1
				input.seek(offset, 2)
	
if __name__ == "__main__":
	main()

```

Then, mad as I was to view the files correctly in Rhythmbox, I did:
```
find music-dir/ -iname "*.mp3" -exec tag-wipe.py {} \;
```

**Use the script at your own risk! I have not tested (obviously) all of my mp3 files after the change.**

---

### Post by r0bb3d on 2008-05-25
Just wanted to say the fix by UlyssesR is great, thanks!

You can test the script on 1 file first by running it like:

' ./tag-wipe.py /home/<user>/Music/<filename>.mp3 '

Once you are confident it doesn't ruin your mp3's (which it shouldn't, all of mine still work fine) you could run it in the way described by UlyssesR.

I can highly recommend this script for getting rid of those damn spooky apetags screwing up your Rhytmbox view ! :)

---

### Post by deruberhanyok on 2008-05-29
Hey All,

I've been running into the same issue (change tag data in rhythmbox, a few seconds later it reverts), though in my case the problem is that I have some MP3 files (downloaded from OC Remix) that have APEv2 tags. EasyTAG is a pretty cool app but when it sees an MP3 file it only lets me edit ID3 data, it won't see the apetag. Even after changing things there the files still won't show properly in Rhythmbox.

I discovered that Winamp is capable of removing APEv2 tags from these files, and it runs through Wine for me without any issues (using 8.04, 64-bit). I can load up Winamp, find the problem file, go into info and just delete all the fields under APEv2 and tell it to not include that tag type.

Hopefully that will be of use to someone.

---

### Post by gmendoza on 2008-07-07
> **UlyssesR said:**
> Well, I have a dirty workaround for this.

Then, I noticed that all files with mismatched tags ended with a TAG'whatever information here' string. ... so I made a dangerous script in python to truncate the mp3 file when it finds this TAG pattern in the end of the file...


UlyssesR,

This was fantastic information, and a great contribution to the community.  Thank you.

I have been running into a number of tag related issues with various players, and noticed quite a few inconsistencies with the way each player handles the tags.  I noticed Rhythmbox would always display the hidden tag, and I was looking for a way to get rid of it.  Your python script did the trick.

For those of you that would like to see this tag information, try the following command:

```
strings songname.mp3 | tail
```

The songs I had issues with contained multiple TAG values, and easytag only seemed to edit the last one.

The following is an example of one song that I had issues with.  Rhythmbox showed the artist as being "The Wailers", when I wanted it to display as "Bob Marley".  The last 4 lines were the only ones of relevence, so I just tailed those for you to see.

```

$ strings 07\ -\ Stir\ It\ Up.mp3 | tail -n 4
TAGStir It Up
The Wailers
Legend
TAGStir It Up  Bob Marley  Legend  2002Amazon.com Song ID: 20254105
```

Using the python script UlyssesR provided, all trailing tag info is cleared.

```
$ ~/tag-wipe.py 07\ -\ Stir\ It\ Up.mp3 
07 - Stir It Up.mp3: found the damn tag - truncating at 0x00a266cb
```

I then used easytag again to reapply the trailing tags, which now look like the following (only showing what's relevant):

```
$ strings 07\ -\ Stir\ It\ Up.mp3 | tail -n 1
TAGStir It Up  Bob Marley  Legend  2002Amazon.com Song ID: 20254105
```

Thanks again, and hope this additional example information is useful for others.

---

