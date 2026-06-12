---
title: "A good ID3 tag organizer?"
date: 2006-06-10
forum: Desktop Environments
---

### Post by CheetahCat on 2006-06-10
Hello Fellas,

I have a large collection (~15,000) of music files (MP3 and DRM-free AAC files) that all have their ID3 tags set correctly. Unfortunately this music is stored in a host of folders that have no real structure.

What I am looking for is a tool that will do the following for me:

[LIST]
[*]rename the audio file based on it's ID3 tags
[*]preserve the suffix depending on the file type (.mp3, .m4u, etc)
[*]create a folder hierachy/structure based on some kind of template (for instance:  /Artist/Album/Title.mp3)
[*]Optionally sorts out duplicates into some kind of duplicate folder for later investigation.
[/LIST]

I searched a lot of places like freshmeat, google, and del.icio.us but i could not find a good tool that reliably does this task. Has someone a hint or suggestion?

Thank you for reading! :)

Best regards,
CheetahCat

---

### Post by Fator dee on 2006-06-10
I'd recommend EasyTAG, it's in the repositories.

---

### Post by blackjack6.21.91 on 2006-06-10
bump

---

### Post by CheetahCat on 2006-06-10
[QUOTE=Fator dee]I'd recommend EasyTAG, it's in the repositories.[/QUOTE]

Thanks for the suggestion. I just spend some time to look into this tool.

It looked promising and feels very native to Gnome, but unfortunately I was unable to do what I described in my first post. Could you describe the steps neccessary to archeive what I had in mind?

CheetahCat

---

### Post by Fator dee on 2006-06-10
[QUOTE=CheetahCat]Thanks for the suggestion. I just spend some time to look into this tool.

It looked promising and feels very native to Gnome, but unfortunately I was unable to do what I described in my first post. Could you describe the steps neccessary to archeive what I had in mind?

CheetahCat[/QUOTE]

Actually I haven't used it to do that kind of thing, but I'll see if I can come up with a solution.

---

### Post by mynimal on 2006-06-10
I'd also be interested in this. This is off subject kinda, but if you ever need an ID3 tag editor I'd highly recommend running mp3tag under wine. It works perfectly, it's free, and it's a great app.

---

### Post by blackjack6.21.91 on 2006-06-10
I like the Audio Tag Tool available in the repos.  I just wish I could use Musicbrainz with it..  But it doesn't organize your library into a heirchy of folders as specified in the first post.  So i suppose this is just another shameless bump.

---

### Post by tronica on 2006-06-10
theres also one called cowbell.

---

### Post by isaacf on 2006-06-27
kyamo looks like it will do the trick. It should be in the repos.

---

### Post by disturbed1 on 2006-06-27
[quote=CheetahCat][LIST]
[*]1. rename the audio file based on it's ID3 tags
[*]2. preserve the suffix depending on the file type (.mp3, .m4u, etc)
[*]3. create a folder hierachy/structure based on some kind of template (for instance:  /Artist/Album/Title.mp3)
[*]4. Optionally sorts out duplicates into some kind of duplicate folder for later investigation.[/LIST][/quote] 
1,2,3. Built in. As soon as easy tag scans a folder, it scans it's ID3 tags. You can set up the renamer how ever you'd like. Let's say I have this folder called /Music. And in that folder are various .mp3 and .ogg files. And I want to do #'s 1,2 and 3. In easytag, under the Misc heading, there is a green icon (a fish maybe ? ;) ) click on it.

Choose rename files and directories from the drop down, and put something like this in the option field
```
%a/%b/%a - %b - %n - %t
``` 
This will create a folder for the artist, inside that folder, create one for the album title, inside of that folder the files will be named artist - album - track## - song title.

So if I have the album Stomp 442 by Anthrax it would be as such -

/home/keith/Music/Anthrax/Stomp 442/Antrax - Stomp 442 - 01 - Random Acts of Senseless Violence.ogg

---

### Post by aysiu on 2006-06-27
TagTool is more native to Gnome than EasyTag is, I think, and TagTool can mass rename songs based on their ID3 tags. I don't know about the folder organization thing, though.

---

### Post by hugmenot on 2006-06-27
This is how it works with Quod Libet. You enter the directory scheme you&#8217;d like and insert the tags as variables with angle brackets.

---

### Post by avender on 2006-07-02
[QUOTE=CheetahCat]Hello Fellas,

I have a large collection (~15,000) of music files (MP3 and DRM-free AAC files) that all have their ID3 tags set correctly. Unfortunately this music is stored in a host of folders that have no real structure.

What I am looking for is a tool that will do the following for me:

[LIST]
[*]rename the audio file based on it's ID3 tags
[*]preserve the suffix depending on the file type (.mp3, .m4u, etc)
[*]create a folder hierachy/structure based on some kind of template (for instance:  /Artist/Album/Title.mp3)
[*]Optionally sorts out duplicates into some kind of duplicate folder for later investigation.
[/LIST]

I searched a lot of places like freshmeat, google, and del.icio.us but i could not find a good tool that reliably does this task. Has someone a hint or suggestion?

Thank you for reading! :)

Best regards,
CheetahCat[/QUOTE]


gmusicbrowser is good one. Get it here [www.gnomefiles.org](www.gnomefiles.org)

mp3tag won't run under wine.

---

