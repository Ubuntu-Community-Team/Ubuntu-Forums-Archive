---
title: "Music Organiser"
date: 2006-02-02
forum: Desktop Environments
---

### Post by tiggsy_mcfiggle on 2006-02-02
I've been using Kubuntu for a few months now, and I've gotten to the point where my music collection really needs organising. I used to use iTunes for windows and seem to remember an 'amalgamate collection' option or something similar. I was wondering if anyone knows of a program to automatically organise my music collection into folders based on their id3 tags? Also does anyone know if the picard program from musicbrainz is any good for filling in missing tags?

Hope you guys can help!

---

### Post by DoorGunner on 2006-02-02
If you like  itunes you will definitely like Amarok. XMMS is also available...it is a winamp type player.

---

### Post by DiscoKiller on 2006-02-02
Amarok will do all of this for you. it is a fine example of a media player. i use it all the time. XMMS is a little too basic for me and doesnt have the funtionality you are looking for. quite a few of the medial player available through synaptic will come with some kind of organiser but i have found Amarok to be by far the best. Enjoy


DK

---

### Post by tiggsy_mcfiggle on 2006-02-02
Could you possibly tell me how to reorganise through Amarok? I've actually been using it for a while and haven't seen anything that looks like the right tool - do I need to install a plugin? Apologies if it's really obvious!

---

### Post by tiggsy_mcfiggle on 2006-02-03
I'm still not having any luck with this - anyone have a suggestion?

---

### Post by DoorGunner on 2006-02-03
[http://www.ubuntuforums.org/showthread.php?t=75588&highlight=install+gstreamer-mad](http://www.ubuntuforums.org/showthread.php?t=75588&highlight=install+gstreamer-mad)

this might help.....

---

### Post by Velvet Elvis on 2006-02-03
When it comes to working with lots of id3 tags, kid3 and JuK are both more powerful, IMHO.

EasyTAG, a gtk ap, is also very good for large batch jobs.

Is the problem that amorok isn't finding all your music?  If the files are properly tagged you should be able to just point it at the right directories in Settings --> Configure --> Collection and then it should organize you music by artist and album.

---

### Post by tiggsy_mcfiggle on 2006-02-05
I think I'm okay with my collection as seen by amarok, the problem is that I have been updating the tags of my collection with easytag and would like to change the structure of my music folder from /music/[artist]/[album]/[track] to /music/[album]/[track] so that my collection will be easier to browse in a portable mp3 player. Any idea if I can automate basically rewriting my music folder into this new format? As I say, I think iTunes organised my music into a directory structure based on tags so I'm looking for a similar program or script/macro.

---

### Post by tiggsy_mcfiggle on 2006-02-06
Anyone have a suggestion? Would really mke my day :D

---

### Post by Velvet Elvis on 2006-02-06
Maybe try asking in the general ubuntu forum?  It will be seen by more people theree.

---

### Post by Harry_Sack on 2006-02-18
I just compiled the newest Prokyon last night, and I think it's the best I've ever seen. I've been missing TGF (TheGodFather) in linux, but it seem I don't need it anyway.

---

### Post by angelillo on 2006-02-21
[QUOTE=tiggsy_mcfiggle]I think I'm okay with my collection as seen by amarok, the problem is that I have been updating the tags of my collection with easytag and would like to change the structure of my music folder from /music/[artist]/[album]/[track] to /music/[album]/[track] so that my collection will be easier to browse in a portable mp3 player. Any idea if I can automate basically rewriting my music folder into this new format? As I say, I think iTunes organised my music into a directory structure based on tags so I'm looking for a similar program or script/macro.[/QUOTE]

Select the ["Collection" browser]("http://docs.kde.org/development/en/extragear-multimedia/amarok/playlist-browsers.html#collection-browser"), on the left of the Amarok window. After that, select the "Group by" drop-down menu, and choose the desired criteria for "Level 1", "Level 2" and "Level 3" submenus. That's it.

---

### Post by the_joker on 2006-10-15
> **angelillo said:**
> Select the ["Collection" browser]("http://docs.kde.org/development/en/extragear-multimedia/amarok/playlist-browsers.html#collection-browser"), on the left of the Amarok window. After that, select the "Group by" drop-down menu, and choose the desired criteria for "Level 1", "Level 2" and "Level 3" submenus. That's it.

Unfortunately, that will only dispay the files in a different manner. If I understand coreectly, the OP wants to completely reorganise the files in the Music folder itself. IE At the moment, all music is stored in **/home/music**, but what we want is music stored by Artist/Album, eg **/home/music/Various Artists/2006 Summer Hits Vol 1/01 - Track Name.MP3**

To do this in Amarok, select all of the music in your collection, click the right mouse button, and select Manage Files/Organize *num* files.

In the new dialog box, select the folder you want to store your music in, mmodify the options as desired, check the Destination Preview to make sure that the folder naming convetions are what you wanted (for instance, when I tried it, Amarok wanted to store music by the Artist's inital, then name. I removed the initial) and select OK.

This will re-organie the physical files on your drive and (optionally) update the cover art as well.

hope this helps :)

---

