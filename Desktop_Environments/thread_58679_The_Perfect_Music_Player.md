---
title: "The Perfect Music Player?"
date: 2005-08-21
forum: Desktop Environments
---

### Post by talkingwires on 2005-08-21
One of things that has frustrated me using Linux is the abscence of a really good music player. Sure, there are lots of music players available for Linux, but each one I've tried seems to be either lacking features, has a bizarre interface, or hasn't been updated in years. It's a shame Winamp's music library doesn't work in Wine, because Winamp does everything I'm looking for. Here's the list:[list][*]A media library.
Who want's to go drilling down through three or four directories to find the song you're looking for?
[*]A great interface.
I want to be able to quickly browse through my Artists and Albums, sorting them as I go. I shouldn't have have to toggle between different views to see my playlists. And I shouldn't see three entries for the same Artist, for example: 'The Cure', 'Cure', and 'Cure ' with a trailing space. in fact words like 'the' and 'and' should be ignored completely.
[*]A customizable interface.
This is important. Just because you like to browse your music a certain way doesn't mean everyone else likes your method. If nothing else, let the user change *something*. I don't know why Rhythmbox even bother's with a 'Preferences' option.
[*]Song ratings, play counts, and dynamic playlists based on criteria I specify.
The ability to save the playlists as a file would be nice, too, in case, *gasp* I want to use them in another program.
[*]Song queues.
Because sometimes I don't want to listen to an entire album, just a bunch of tracks.
[*]Portable player support.
Syncing with a local database is crucial. My music library recently passed the 20gb mark. When I go into GTKpod, how in the hell am I supposed to remember the individual files I've added recently? Plus, iTunes and Winamp keep track of your music's play counts and ratings in a local database, so you can create dynamic playlists excluding music you've listened to recently.
[*]Music library management.
Great, I've got twenty 'Artist Foo - Track 01' files under 'Unsorted'. Can I edit the tags, please?
[*]Renaming of files based on the tags.
Winamp can't do this, and I haven't found a plugin that does it, either. So, this one is up for grabs. Hell, I stuck with MusicMatch for a long time because it was the one music player/manager I found that could do this. Having properly named files is crucial, because:
[*]Playlist burning.
Okay, I've got this killer mix. Now I have to drill down through my folders, looking for each track so that I can burn it in a seperate program. Ugh.
[*]A good plugin interface.
Because sometimes you just can't anticipate what each user wants out of your program. And if you could, would you really want that much bloat? Oh, and please, have a friendly way to manage the installed plugins. Having to manually launch a program through the commandline really doesn't qualify as a plugin, does it Rhythmbox?
[/list]Bonus Round:[list][*]Use a  desktop-environment-neutral toolkit.
"Hey, I've made this awesome music player, but to use it you'll have to load 80mb of libraries for a desktop environment you don't even use into your memory!" Plus, hey, it's portable to other OSs!
[/list]
With the exception of one point, Winamp has had all these features for years. Musicmatch and iTunes do most of them. So why can't I find a music player on Linux that matches more than two or three of them? Is anyone else out there as frustrated as I am?

---

### Post by adwait on 2005-08-21
I suggest amarok.......its the best I have tried. Juk was also good, but I couldn't get it to work properly.......

---

### Post by Hairy_Palms on 2005-08-21
musicmatch is possibly the crappest, crashiest music player ever imo it was ok till about version 7.0 then it just got shit.
try beep music player, it has some really nice skins you can save playlists as files and you can edit tags by right clicking on the song in the playlist it also has a great plugin interface. it doesnt have a music library though, but as i came from musicmatch i save all my music in musicmatchstyle directories by artist and album. afaik gtk pod is the only one that supports ipod syncing but you can open xmms and beep music playlists in gtkpod

or i recommend trying zinf, its available in the ubuntu repos its available for windows its fully skinnable and it plays every music file ive ever thrown at it 
it has a good media library too that arranges music by artist,album, or alphabetically depending how u tell it, 

or a third alternative is to aquire a copy of crossover office which runs itunes on my bros pc when i convinced him to switch to suse. it runs itunes fine,

---

### Post by lothar_m on 2005-08-21
There are allready a zillion treads about music players for linux in this forum.....

You just had to open another one.........

---

### Post by doclivingston on 2005-08-21
How do you define "Really good music player"? Different people want different things from their music player, and this is why so many exist for Linux. As someone who has done some development on a linux music player, I've seen user requests like "Add feature X" and "Add feature Y" where X an Y are the exact opposite of each other - you can't make everyone happy.


The "sorting without the 'The'" is a hard problem in general. If you have that in English, why not support it in other languages? which leads to the problem of not knowing whether a word is an article or not - how do you differentiate between "Die Aerzte" (where "Die" is a German article, similar to "The") and "Die Happy" (where it is a normal word)? Also how do you deal with the fact that "The" might be in the name of a foreign band, but not the English word "The" (in which case it shouldn't be ignored)? You can't only apply it based on the locale the user uses, because the user may have songs from other languages in their library (e.g. I have few German bands in my library).

A customisable UI can be good, but it can also leads to accessability problems and the like. You need to put some limits on flexability, and it really depends on the design of the player - what kind of thing are you looking for in a "flexable interface" player?



Specific to Rhythmbox:
* 0.9.0 has playlist burning support
* 0.9.0 has partial tag-editing support, although it doesn't yet work for Oggs and isn't compiled in by default
* Improved automatic playlists (more criteria, sorting, etc) has been implemented, and should hopefully be in 0.9.1
* Several other features you want are good, and would be nice if RB has them, but it doesn't (yet). Some of them (particularly the queue, and cover art) are half-done, but need a bit of work; others (such as plug-ins and better player support) we have plans for, but have other things to get done first.
* The code that makes RB have the iTunes-esque "Source list on left, browsers on top, track list below" kind of layout is only a _very_ small part of the code, and is completely seperate from the rest of RB. If I had the inclination (which I don't really) I could probably change RB to be a Muine (easier) or BMP (harder, but not that hard) look-alike in a day or two.

---

### Post by slux on 2005-08-21
Some good points. I especially liked the one about how slightly varying artist tags should be combined, go file a RFE for AmaroK or something. :P

Now, I'd recommend AmaroK as well. Not that it does everything you listed but it has some of those and also some other nice tricks up it's sleeve that I haven't been able to find in other players.

For renaming of the files based on tags I'd suggest using a separate program for now although that too is very much a valid RFE. The only feature I really disagree with is your preference of a DE neutral toolkit. It's a bit of a letdown when it happens to support the one that you're not running but there are still some benefits and in the long run it would certainly be preferable for the need to set all the exact same preferences in a zillion apps to go away. I'm willing to sacrifice 100MB for the convenience of only having to look in two places and I see some hope that the freedesktop initiative will make that one place.

That said, AmaroK is very much a KDE program, to the point that it uses Konqueror features for ripping and K3B for burning. Being a GNOME user that's not my favourite part of it, but K3B is the best burning app I know of anyway and hey, nothing's perfect.

---

### Post by doclivingston on 2005-08-21
I'd have to agree that amaroK is the most featureful Linux music player. I haven't actually seen any music player that renames files for you, I've always found EasyTag to a fairly good tag editor, although it's interface could be a bit better.

I agree with slux about not using DE stuff - if you don't use either the Gnome or KDE platforms, you will either miss out on some feautes they provide (using remote filesystems, accessability support, etc) or have to re-implement them in the application (poorly). On the good side GStreamer is shaping up well as a desktop-neutral media backend - Gnome uses it, the KDE people are considering it for KDE4 and the amaroK and JuK developers recommend it anyway.

Also as slux said, it's worth filing RFEs (Request For Enhancement) with your suggestions against the various media players, assuming they haven't been files already. I'm sure most of them have been, but they might not have, and you might be able to offer some furthur ideas on how the features should work.

---

### Post by bionnaki on 2005-08-21
I have been using rhythmbox & I enjoy it. but I need to see bitrate info. what player does this besides xmms?

---

### Post by manicka on 2005-08-21
amaroK

---

### Post by Sephiriz on 2005-08-21
As many have said, amaroK does all that you specify.  It is, in fact, the greatest (in my opinion) music player for Linux, even when you use GNOME.  Now, my personal complaint, which I and many others have voiced before, is amaroK's inability to work with file tags from m4a encoded music.  Mind you, it can still play those songs, just not organize them coherently in the music library.  Even with this issue, I still use amaroK and simply suffer the lack of a few hundred songs in my library (which is breaking like, 4500 different tracks).

---

### Post by slux on 2005-08-22
[QUOTE=doclivingston]I'd have to agree that amaroK is the most featureful Linux music player. I haven't actually seen any music player that renames files for you, I've always found EasyTag to a fairly good tag editor, although it's interface could be a bit better.
[/QUOTE]

Well, In my opinion it's actually the most featureful music player that exists *on any platform* :)
At least I've not found anything as good on Windows or Mac OS X so far even though I looked around a bit just to know what's available.

---

### Post by Mogomotsi on 2005-08-22
Help me I may help you

I am new to lunix but back in my Windows days I developed a nice MP3 player with all features you require is there a software I can Download to and use to make VB Applications work with Ubuntu. i am willing to share this application if it can work.

---

### Post by talkingwires on 2005-08-22
[QUOTE=Hairy_Palms]musicmatch is possibly the crappest, crashiest music player ever imo it was ok till about version 7.0 then it just got shit.
*...* 
or a third alternative is to aquire a copy of crossover office which runs itunes on my bros pc when i convinced him to switch to suse. it runs itunes fine,[/QUOTE]I agree. Version 7 was the first "music manager" I ever used, and I really liked some of its features. The Tag Lookup and Multi-tag Editting were great. But it was slow, lacked plugins, and each version after 7 got progressively worse. I kept it on my Windows partition solely for it's music management features, and used Winamp for everything else. Then I discovered [Helium](http://www.helium2.com/).

I don't really like iTunes. It's slow, and only really manages your music if you give it complete control over your file names and directories. Smart Playlists really rock, though.

---

### Post by talkingwires on 2005-08-22
> **doclivingston]How do you define "Really good music player"? Different people want different things from their music player, and this is why so many exist for Linux. As someone who has done some development on a linux music player, I've seen user requests like "Add feature X" and "Add feature Y" where X an Y are the exact opposite of each other - you can't make everyone happy.[/QUOTE]I think I just defined my idea of a really good music player.  said:**
> 
[*]BMP fixes the bugs and provides a better user interface for XMMS, without bringing anything new to the table.
[*]XMMS, whose development has been halted, was a clone of Winamp 2.
[*]Winamp 2 is the old branch of Winamp, and is also not being activily developed.

(Side Rant: Winamp 2 is a wholely unremarkable music player, other than it was the "first" to have some of its features. It has been surpassed any number of other players, whether they aim to be light-weight [Foobar] or play numerous file types and manage collections of music [umm, Winamp 5]. Why so much effort has been expended to clone it is beyond me.)
[/list]There are other examples, like Rhythmbox. Each new version brings it closer and closer to being a clone of iTunes (that supports OGG). Where's the innovation?


[QUOTE=doclivingston]The "sorting without the 'The'" is a hard problem in general. If you have that in English, why not support it in other languages?GTKpod solved this quite easily: you provide you own list of words to filter out. Of course, letting the user input his or her choice of words in Rhythmbox would mean creating an actual 'Preferences' panel. :?

[QUOTE=doclivingston]Specific to Rhythmbox:
* 0.9.0 has playlist burning support
* 0.9.0 has partial tag-editing support, although it doesn't yet work for Oggs and isn't compiled in by default
* Improved automatic playlists (more criteria, sorting, etc) has been implemented, and should hopefully be in 0.9.1
* Several other features you want are good, and would be nice if RB has them, but it doesn't (yet). Some of them (particularly the queue, and cover art) are half-done, but need a bit of work; others (such as plug-ins and better player support) we have plans for, but have other things to get done first.[/QUOTE]That's really great to hear, especially the part about the queue. But right now, I'm frustrated by its limitations, which was why I started this thread. Anyway, I'll definately be checking out future versions of Rhythmbox when some of these features get implimented.

---

### Post by talkingwires on 2005-08-23
[QUOTE=slux]
*...*
Now, I'd recommend AmaroK as well. Not that it does everything you listed but it has some of those and also some other nice tricks up it's sleeve that I haven't been able to find in other players.
*...*
[/QUOTE]
I remember using AmaroK back in my SuSE days, but stopped when I switched to Ubuntu, being Gnome-centric and all. But you've piqued my interested, and I'll try it out. Thanks!


[QUOTE=doclivingston]
I haven't actually seen any music player that renames files for you, I've always found EasyTag to a fairly good tag editor, although it's interface could be a bit better.
*...*
[/QUOTE]
Well, there is MusicMatch (Windows only). But as Hairy_Palms mentioned, the program tends to be, well, otherwise pretty crappy. And I agree. I detest EasyTag, and find its name to be somewhat of a misnomer. May I recommend [Quod Libet and Ex Falso](http://www.sacredchao.net/quodlibet)?

[QUOTE=doclivingston]
*...*
I agree with slux about not using DE stuff - if you don't use either the Gnome or KDE platforms, you will either miss out on some feautes they provide (using remote filesystems, accessability support, etc) or have to re-implement them in the application (poorly).
*...*
Also as slux said, it's worth filing RFEs (Request For Enhancement) with your suggestions against the various media players
*...*
[/QUOTE]Good points. And maybe I should start being a more active user in OSS development, moving past just being a end-user and such. Good ideas.


[QUOTE=Sephiriz]
Now, my personal complaint, which I and many others have voiced before, is amaroK's inability to work with file tags from m4a encoded music.
[/QUOTE]I only have a few m4a files, but I can see how this would be frustating to other users. Why don't they support that format?


[QUOTE=Mogomotsi]
I am new to lunix but back in my Windows days I developed a nice MP3 player with all features you require is there a software I can Download to and use to make VB Applications work with Ubuntu. i am willing to share this application if it can work.[/QUOTE]I'm not really sure, as I'm not a developer. Your best bet would probably be [Mono](http://www.mono-project.com/Main_Page), as it aims to recreate Microsoft's .NET platform in Linux. As I understand it, Visual Basic was assimilated into the platform with the release of Visual Studio 2003/.NET. Then again, I may be completely off-base here. If nothing else, perhaps it would run in [Wine](http://winehq.com/)?

If your program supports all those features, I'd love to try it out, even if only in Windows. Could you send me a link?

---

### Post by doclivingston on 2005-08-23
[QUOTE=talkingwires]I detest EasyTag, and find its name to be somewhat of a misnomer. May I recommend [Quod Libet and Ex Falso](http://www.sacredchao.net/quodlibet)?[/quote]
I'd have to agree here - the only real good point about EasyTag is that it works. trying out Quod Libet and Ex Falso is something that I've been meaning to do for a while.

[QUOTE=talkingwires]Good points. And maybe I should start being a more active user in OSS development, moving past just being a end-user and such. Good ideas.[/quote]
If you do plan on developing a music player, please consider helping one of the existing ones to make it do what you want rather than starting a new one - there is already way too much code duplication amongst the music players, and people making the same mistakes over and over again. Most of the "modern" music players (amaroK, Rhythmbox, the "next-gen" BMP and probably several other ones I haven't tried) are extremely flexible and could easily be modified to do what you want, even if that flexability isn't obvious as a user.

[QUOTE=talkingwires]I only have a few m4a files, but I can see how this would be frustating to other users. Why don't they support that format?[/quote]
I believe it is because TagLib, which amaroK uses, doesn't support reading tag from m4as. Why it doesn't have m4a support, I'm not sure.

This is the reason that Rhythmbox uses GStreamer to read tags, as well as for playback, because it guarantees that any file you can play will have its tags read (and vice versa). The downside to using GStreamer for tag reading/writing is that tag reading is slower than with TagLib and it doesn't (yet) have tag writing support some some media types. GStreamer's tag reading speed could be improved, but will never be quite as fast as a dedicated tag-reading library because of the way it does some things (it's stream based, so will read more of the file, etc).

---

### Post by doclivingston on 2005-08-23
> **talkingwires]GTKpod solved this quite easily: you provide you own list of words to filter out. Of course, letting the user input his or her choice of words in Rhythmbox would mean creating an actual 'Preferences' panel. :?[/quote]
Yeah, that could work. It doesn't help with the case I mentioned above, but I don't think anything for of a multi-lingual natural language parser that can determine the language that every single name is in, will be able to figure that one out  said:**
> That's really great to hear, especially the part about the queue. But right now, I'm frustrated by its limitations, which was why I started this thread. Anyway, I'll definately be checking out future versions of Rhythmbox when some of these features get implimented.

A lot of Rhythmbox limitations aren't limited by it's code or design, but by it's user interface. If someone can think of a way to put those features in the UI, without making it cluttered and overly complicated (which is my main complaint against amaroK), I'm sure the RB developers will listen.

As an example, take the queue idea. The problem that we (the RB developers) had was that there are two different use cases for the queue:
1) queueing up lots (20, 50, 100 or whatever) of songs and almost always playing from the queue. This is good for parties and the like.
2) queueing up one, or a small number of songs and usually playing from the library or a playlist. This is good for saying "I want this/these song(s) to be played next".

Unfortunately the user interface is fairly different for these two use cases, and users seem to be split 50-50 on which should be implemented. If we implemented the UI for (1), it's awkward to try to use it for (2). If we implemented the UI for (2) trying to do (1) become pretty much impossible with the queue, although it can be approximated by using a using a simple playlist (which kind of works, but not completely).

---

### Post by Hairy_Palms on 2005-08-23
theres 2 options afaik if u wanna vb in linux either gambas or mono as talkingwires said.
although i beleive REALBasic is available for linux too, although thats not free youll either have to buy or aquire it somehow

---

### Post by plb on 2005-08-23
Amarok 1.3 is probably the best player out atm, although xmms2 looks promising  ;-)

---

### Post by bionnaki on 2005-08-23
I have tried amarok the past few days - I dont like it. Way too cluttered and bloated-feeling. When I was using Windows XP, I was a Foobar2000 person - I liked it because it was lightweight, loaded instantly, nearly 100% customizable, played every file type, and displayed every bit of information you'd want (bitrate, length, ID tags, etc). [http://www.foobar2000.org](http://www.foobar2000.org)

*That* was my perfect music player - hopefully I can find something similar. Surely there must be a linux player for audiophile nerds  :)

---

### Post by junior aspirin on 2005-08-23
i used to use [musikCube](http://www.musikcube.com/) on windows and i miss it. it is very similar to rythmnbox, but much more customiseable and faster. the developer does plan to releace a linux version (musikBox) but when and if it will be officaly developed is anyones guess. im have installed it from cvs but it was hard to install and is slow and very basic.

on a good note it is opensource and they would probably welcome any help :) i jst wish i knew how to program, will be sticking to muine untill then.

---

### Post by bionnaki on 2005-08-23
speaking of foobar, why hasnt it been ported?

---

### Post by shanghaipi on 2005-08-23
I also used musikcube.  I think amarok is a pretty good alternative, but I miss that program so much.

---

### Post by talkingwires on 2005-08-23
[QUOTE=junior aspirin]i used to use [musikCube](http://www.musikcube.com/) on windows and i miss it. it is very similar to rythmnbox, but much more customiseable and faster.[/QUOTE]
Have you looked at [wxMusik](http://musik.berlios.de/)? It is a fork of MusikCube that is based on wxWidgets. It came about around the time the Linux version of MusikBox/Musik/whatever it was called at the time stopped being updated. I don't think the developement is as active, as the screenshots look like the version of MusikCube I used over a year ago.

---

### Post by shanghaipi on 2005-08-23
Actually, Wxmusik was Casey Langdon's first major attempt at a music player.  He and the current upkeeper of WxMusik created it, but Casey wanted to start over and create a better player.  The person who is upkeeping WxMusik didn't want to start over, so Casey and him went their seperate ways and Casey created Musikcube.  At least, this is what is on the forums and according to Casey.

But, no, i haven't tried it, only Musikcube.

---

### Post by pixeltarian on 2007-05-23
wxmusik is the best player for linux I've run into. the only think I don't like is that lack of development interest. it's been over a year since the last release...

---

### Post by TheMono on 2007-05-23
Please don't gravedig old threads! It may have been over a year since the last release of wxmusik, but it's also been over a year since the last post in this thread!

---

### Post by Fayte2071 on 2007-05-24
Nah, I'm glad people bring back certain old threads. I just recently got into Linux/Ubuntu and music is a big deal to me; I'm glad I got to see this because I don't want to stick with just Rhythmbox

---

### Post by onbongos on 2007-05-24
i like sonata/ncmpc + mpd or moc. there is exaile, a gtk clone of amarok but it's very crashy for now ime

---

### Post by BLTicklemonster on 2007-05-24
> **TheMono said:**
> Please don't gravedig old threads! It may have been over a year since the last release of wxmusik, but it's also been over a year since the last post in this thread!
But this is still relevant, at least to the grave digger. I'd never heard of this program before, and now will check it out due to this revival. Kudos to the necrothreadreviver. There's a forum I go to where if someone DARES to dig up an old post, the admins come unhinged and act all stupid about it. Okay, I used to go there, but I avoid it like the plague these days, even though it's a forum for a community that I contribute to in useful ways.

---

### Post by aroch1 on 2007-05-24
AmaroK!!!  I even use it in GNOME, cause theres no better GTK+ apps

---

### Post by pixeltarian on 2007-05-25
I realize it's dumb to "gravedig" old posts, but this really is my favorite music player ever. I even 
use it on windows instead of musikcube. I was hoping some bored programmer would see this post and decide to help with the development. well, not really. I guess mostly just fantasized about it...

---

