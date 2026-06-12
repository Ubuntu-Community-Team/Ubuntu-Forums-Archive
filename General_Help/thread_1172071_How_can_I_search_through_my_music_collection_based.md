---
title: "How can I search through my music collection based on file metadata?"
date: 2009-05-28
forum: General Help
---

### Post by SplinterOfChaos on 2009-05-28
What I want to do is open my music folder, which contains many kinds of media formats instead of just mp3, and do something along the lines of *ls* or* find **artistname* to print out all the files matching that description.

I actually have seen a few good options out there, but they were all gui apps, which defeats the purpose of trying to use the command line. Also, they were made more for editing ID3 tags, but that's acceptable.

A solution that only works on mp3s is acceptable, though one that works on many file types is preferred.

Thank you.

---

### Post by salvachn on 2009-05-28
Maybe you can write an sed/awk script of your own? Just kidding, but a nice idea to get me started on developing something! I'll get back soon after my term-end exams are over next week. :)

---

### Post by SplinterOfChaos on 2009-05-28
Cool.

I'm thinking I'd want to call it something like this:

$ cd music-folder
$ ls | the-prog -artist 'an artist' -album 'an album'

I suppose it wouldn't actually be a difficult script to write, assuming there's a good library out there that handles the metadata in a sane manner.

---

### Post by salvachn on 2009-05-28
I was talking about handling metadata. LOL. Need some work to keep myself occupied during the vacation. Will start next week and up it to launchpad soon.

---

### Post by gibbylinks on 2009-05-28
I think "Amarok" music palyer allows searches like this.

It reads all the files into a library, and I'm pretty certain you can then search for various things.

---

### Post by kpkeerthi on 2009-05-28
@SplinterOfChaos
I saw your post and thought I could come up with something like this:
```

media-find: Finds media files based on ID3 meta-data
	
Usage: media-find /path/to/search [OPTIONS]
		
OPTIONS:
-f file-name-pattern
     File name pattern to search for. Defaults to "*" (all files), when not specified.
					
-v id3-tag-version 
     One of the following values can be used as an argument to this option:
   1  Read ID3v1.x tags only
   2  Read ID3v2.x tags only
   Defaults to 1, when not specified, in which case ID3v1.x tags will be searched.
				
-a artist. The argument can be specified in full or part or as a regular expression.

-A album. The argument can be specified in full or part or as a regular expression.

-t title. The argument can be specified in full or part or as a regular expression.
				
-g genre. The argument should be a valid genre string or number. 
				
-c comment. The argument can be specified in full or part or as a regular expression.
				
Examples:
		
1. media-find /path/to/search -f "*.mp3" -a "Michael Jackson"
 - Lists all mp3 files tagged with artist Michael Jackson.
			
2. media-find /path/to/search -a "Michael Jackson" -A "Thriller"
 - Lists all media files tagged with artist Michael Jackson and album Thriller

3. media-find /path/to/search -t "Rhythm Devine" -a "Enrique"


```

---

### Post by SplinterOfChaos on 2009-05-28
> **gibbylinks said:**
> I think "Amarok" music palyer allows searches like this.

It reads all the files into a library, and I'm pretty certain you can then search for various things.

It does not appear to, from the command line, although yes I believe you're right from the gui program. On the other hand, it takes a looong time to start and doesn't always work, for whatever reason, so I try not to use it.

---

### Post by mcduck on 2009-05-28
You pretty much need to have some sort of database of your files to do that, otherwise it would require reading through the metadata from every single file every time you want to do a search..

If you just want a command-line based music player/database you might want to try MPD with either MPC or NCMPC as client.

---

### Post by SplinterOfChaos on 2009-05-28
I'm ok with that. I think I'd prefer it [edit]NOT[/edit] to do a DB, which would have to constantly be checking if any of the data was changed/added/removed anyway. Besides, I don't have any exp programming DBs, but I'd think it'd be harder to program.

---

### Post by mcduck on 2009-05-31
> **SplinterOfChaos said:**
> I'm ok with that. I think I'd prefer it [edit]NOT[/edit] to do a DB, which would have to constantly be checking if any of the data was changed/added/removed anyway. Besides, I don't have any exp programming DBs, but I'd think it'd be harder to program.

Actually database would be better, as it would only have to update information about new, or changed, files instead of all files. And having a database doesn't mean it would have to be constantly updated, only when there's really a reason to update it.

But it's true that a database would be harder to program. Of course that's only an issue if you want to make your own program for this instead of using some existing one.

For example MPD has a great database with excellent command-line interfaces available. That's what I'd use for this kind of purposes.

(I just tested searching from MPD database with MPC ("mpc search artist Anthrax"), I have 45GB of music and listing all tracks from from the specified artist took 0,043 seconds.. Doing the same by reading through the whole music collection to gather the required metadata would definitely take something closer to 10 minutes, at least. ;)

---

### Post by Legace on 2009-05-31
Why don't you use something like pyRenamer to rename all your music files logically so that you can easily search your music through CTRL + F?

---

### Post by SplinterOfChaos on 2009-05-31
Since my purpose is LISTING the files, although I do have need of a renamer, what I could maybe do is steal some of the pyrenamer source code and write my own wrapper to interact with it entirely from the console.

Sounds more fun and less bug-worthy than writing one myself, no?

---

