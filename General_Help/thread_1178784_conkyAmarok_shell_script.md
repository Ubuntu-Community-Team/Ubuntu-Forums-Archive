---
title: "conkyAmarok shell script"
date: 2009-06-04
forum: General Help
---

### Post by TheSeanKelly on 2009-06-04
Sorry if this is a poor choice of forum to post this on; I posted it here because this is where the thread for conkyExaile and conkyForecast are.

_The conkyAmarok Script_
I used the conkyExaile script located [here]("http://ubuntuforums.org/showthread.php?t=926041") for a period of time, and then decided amarok plays MUCH nicer with my iPod.  However, I still wanted the nice conky integration I got.

I found a conkyAmarok script [here]("http://www.linuxforums.org/forum/linux-programming-scripting/127426-dcop-amarok-scripts.html") by eirc.

However, this script lacked many features I wanted to use, so I added functionality for rating, status, current time, total time, and year.  I also cleaned up how the script looks when conky is either not playing anything, or not running whatsoever.

I haven't REALLY tested anything to do with collection info or collection stats, but they all seem to work in a terminal.

Here's the help output seen when "conkyAmarok help" is run:

```

USAGE
In terminal:	/path/to/conkyAmarok <data_type>
In conky:	${execpi <update time in seconds> /path/to/conkyAmarok <data_type>

EXAMPLES
/home/sean/bin/conkyAmarok title
${execpi 1800 /home/sean/bin/conkyAmarok title}

=================================================================================== 
Choose data_type from the following:

SONG INFO               
album			 (Album title)
artist			 (Artist name)
genre			 (Genre)
playCount		 (Number times song has been played)
progress		 (Percentage time elapsed)
rating			 (Out of 5 stars)
score			 (Amarok's intelligent scoring system)
status			 (Playing/Paused/Stopped/Not Running)
title			 (Track title)
track			 (Track number)
trackCurrentTime	 (Current position in track)
trackTotalTime		 (Total time of track)

COLLECTION INFO
totalAlbums		 (Total number of albums in colleciton)
totalArtists		 (Total number of artists in collection)
totalCompilations        (Total number of compilations in collection)
totalGenres	 	 (Total number of genres in collection)
totalTracks    		 (Total number of tracks in collection)

COLLECTION STATS
most_songs_by_artist	 (Name of artist with most songs)
most_songs_by_artist_n	 (Number of songs by that artist)	
most_songs_are_genre	 (Genre with most songs)
most_songs_are_genre_n	 (Number of songs in that genre)
most_songs_during_year   (Year with most songs)
most_songs_during_year_n (Number of songs in that year)
===================================================================================
```

I've also attached a screenshot of my desktop using the script, as well as the script itself.  (NOTE!!!  I had to upload it as "conkyAmarok.sh" because the forum won't let me upload a file without an extension.  Just rename it to conkyAmarok.)

I suggest putting the script in ~/bin or /usr/local/bin or something, so conky can just call it with conkyAmarok instead of /path/to/conkyAmarok.

Any questions, comments, corrections welcome; this was just as much an exercise in shell coding as it was me wanting to make something work better; I'm not very experienced. 

Sean

---

