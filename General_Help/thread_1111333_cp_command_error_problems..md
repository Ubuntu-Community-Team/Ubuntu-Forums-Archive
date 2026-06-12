---
title: "cp command error problems."
date: 2009-03-30
forum: General Help
---

### Post by casbahdk on 2009-03-30
I recently ripped most of my CD collection as .flac files and filled-up the hard disk on my laptop. I would like to copy them over to an external USB drive, but I get the following errors:

```
$ cp -a ~/music /media/STEALTH
cp: cannot create regular file `/media/STEALTH/music/Pink Floyd/The Wall/02 - Is There Anybody Out There?.flac': Invalid argument
cp: cannot create regular file `/media/STEALTH/music/Pink Floyd/The Wall/01 - In the Flesh?.flac': Invalid argument
cp: cannot create directory `/media/STEALTH/music/Spandau Ballet/Gold: The Best of Spandau Ballet': Invalid argument
cp: cannot create directory `/media/STEALTH/music/Tears for Fears/Tears Roll Down: Greatest Hits 82-92': Invalid argument
cp: cannot create regular file `/media/STEALTH/music/Bob Dylan/At Budokan/10 - Is Your Love in Vain?.flac': Invalid argument
cp: cannot create regular file `/media/STEALTH/music/Rick Nelson/Poor Little Fool/13 - Got A Feeling (:ive).flac': Invalid argument
cp: cannot create regular file `/media/STEALTH/music/Carole King/Tapestry/09 - Will You Love Me Tomorrow?.flac': Invalid argument
cp: cannot create regular file `/media/STEALTH/music/Vaya Con Dios/The Best of Vaya Con Dios/08 - What\'s a Woman?.flac': Invalid argument
cp: cannot create directory `/media/STEALTH/music/Steely Dan/Showbiz Kids: The Steely Dan Story': Invalid argument
cp: cannot create regular file `/media/STEALTH/music/Phil Collins/But Seriously/03 - Do You Remember?.flac': Invalid argument
cp: cannot create directory `/media/STEALTH/music/Jethro Tull/Too Old to Rock \'n\' Roll: Too Young to Die!': Invalid argument

```

Can someone please tell me what is going on and what I need to do to get all of the files copied?

Cheers

---

### Post by kanikilu on 2009-03-30
I'm not sure, but I don't think it's any coincidence that all those files have a special character in their path (e.g. ?, !, (), :, etc.).

Maybe try replacing or removing those characters?

---

### Post by 3Miro on 2009-03-30
Try using nautilus. To see hidden folders, press Ctr + H.

---

### Post by casbahdk on 2009-03-30
> **3Miro said:**
> Try using nautilus. To see hidden folders, press Ctr + H.

There are no hidden folders.

---

### Post by 3Miro on 2009-03-30
> **casbahdk said:**
> There are no hidden folders.

Either way, doesn't it work from within nautilus? The problem looks like it is the name of the file, it contains special characters.

---

### Post by casbahdk on 2009-03-30
> **kanikilu said:**
> I'm not sure, but I don't think it's any coincidence that all those files have a special character in their path (e.g. ?, !, (), :, etc.).

Maybe try replacing or removing those characters?

If I do that, I change the names of the songs. I used Sound Juicer to rip these songs; if this were a general problem, one would think that something would be done to transparently change file names without changing the names of the songs as they are being ripped. As it is, there are 104 files that need to be changed by hand.

---

### Post by CatKiller on 2009-03-30
> **casbahdk said:**
> I would like to copy them over to an external USB drive

Your external drive is formatted as FAT or NTFS, and neither of those are able to contain files that have those characters.

Your only options really are to either format the drive to a more robust filesystem (the only character you cannot use in a filename on an ext3 filesystem is /, but you need a free driver to be able to read an ext filesystem from Windows) or to rename those files. There are a number of utilities that will automatically rename the files to exclude Windows' "special" characters. I know Amarok and Easy Tag can do it, but I'm sure others can too.

EDIT:
> **casbahdk said:**
> If I do that, I change the names of the songs. I used Sound Juicer to rip these songs; if this were a general problem, one would think that something would be done to transparently change file names without changing the names of the songs as they are being ripped. As it is, there are 104 files that need to be changed by hand.

You're only changing the filenames of the files. The song names will still be expressed correctly in the metadata tags for the songs, which is what most sensible players use to identify the songs anyway. You don't need to do it by hand. Most tools that are set up to use a library of songs understand that this is sometimes necessary, and so provide a means to do it automatically. And I'm pretty sure that Sound Juicer can be configured to exclude the "special" characters in the first place.

EDIT 2: Yep. From the Sound Juicer Preferences help page:

> Select the **Strip special characters** check box to make Sound Juicer remove or replace characters such as spaces and punctuation in the filenames. This is useful if you plan to put the audio files onto a portable device or another computer which has more limitations on file names.

---

### Post by casbahdk on 2009-03-31
Yes, the external drive is formatted as FAT 32. I was hoping to be able to transfer the files to my Mac (OS X Leopard / Ubuntu Intrepid Ibex PPC dual boot). I am trying to gradually migrate to a Linux only environment.

OK, I had no idea that this was an issue or I would have made sure that Sound Juicer prefs were set to strip the illegal characters.

I just installed EasyTag. How do I get it to strip those characters from the file names in my collection of .flac files? There isn't any help file and nothing helpful on the man page either.

Cheers

---

### Post by CatKiller on 2009-03-31
> **casbahdk said:**
> I just installed EasyTag. How do I get it to strip those characters from the file names in my collection of .flac files?

Set it to do so in the preferences, and then I think it's Scan Files. You can either have the scanner set to fill in tags based on the filename, or change the filename based on the tags. It is a bit clunky-looking, but it's quite good once you get the hang of it.

---

### Post by casbahdk on 2009-03-31
> **CatKiller said:**
> Set it to do so in the preferences, and then I think it's Scan Files. You can either have the scanner set to fill in tags based on the filename, or change the filename based on the tags. It is a bit clunky-looking, but it's quite good once you get the hang of it.

I think Sound Juicer filled in the original tags correctly, so I only want to strip the illegal characters from the filenames with EasyTag.

---

