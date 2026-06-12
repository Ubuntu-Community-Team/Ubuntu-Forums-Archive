---
title: "Discussion - https://help.ubuntu.com/community/PlayMusicFromCommandLine"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by Elfy on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/PlayMusicFromCommandLine](https://help.ubuntu.com/community/PlayMusicFromCommandLine)

Support threads should be posted in normal forums.

Thank you.

---

### Post by shantiq on 2012-06-29
thanx elfy

made 3 small adjustments since text was from a year ago or so


1.  for two tone   using nvlc --nocolor
2.  using gnome-open-terminal as another option to nautilus-terminal
3.  info about setting hotkeys for nvlc

---

### Post by Elfy on 2012-06-29
thanks :)

---

### Post by sysaxed on 2012-07-06
Please add moc! It's much better choice for playing music from the terminal.

```
sudo apt-get install moc
mocd
```

---

### Post by Toz on 2012-07-06
Some comments:

1. The first section is specific to ubuntu - xubuntu, kubuntu, lubuntu users will not have nautilus installed. Its also possible that installing nautilus-terminal will also install nautilus (unable to verify) which might cause problems on some (ie. xubuntu). Perhaps specifying that these instructions are for ubuntu only or adding similar instructions for the other spins.

2. In addition to sox, I would also add mpg123/mpg321. The nice aspect of this player is that:
```
mpg321 -Zz ~/Music/*.mp3
```
...will repeat-random play all files that match that pattern. Ctrl-C to skip to next tune, Ctrl-Z to pause, fg to un-pause and 2 Ctrl-Z in quick succession to quit. Unfortunately, it lacks some other abilities like previous, forward/backward x frames, etc, but is a quick, small player. It can also stream online radio via something like:
```
mpg321 -vC http://72.232.2.83:80
```
...(dubstep radio station in the example above)

3. And as suggested by sysaxed, there are also ncurses-based music players. They are lighter than their graphical cousins, but offer more control and functionality than just the command-line utilities. If you choose to mention them, in addition to moc, you could add cmus, mp3blaster, cplay. I'm not sure about moc or mp3blaster, but both cmus and cplay have remote control utilities that you could assign to shortcut keys and be able to manage the playlists in that manner.

---

### Post by sysaxed on 2012-07-06
> **Toz said:**
> 

2. In addition to sox, I would also add mpg123/mpg321. 
...
Unfortunately, it lacks some other abilities like previous, forward/backward x frames, etc, but is a quick, small player. 
If you add -C parameter to mpg123 then you're able to use all these features you mentioned. Try it.
```
mpg123 -ZzC ~/Music/*.mp3
```now if you press "h" button you'll get all possible options. Some of those are:
[f]    next track
[d]    previous track
[:]    fast forward
[;]    fast rewind


By the way, what is the difference between mpg123 and mpg321?

---

### Post by Toz on 2012-07-06
Cool, thanks. My understanding is that mpg123 is non-free (in that you can't distribute the code) whereas mpg321 is the opensource version.

---

### Post by vasa1 on 2012-07-06
First, nice wiki! ```
mplayer *
``` is something even I can do.

> **Toz said:**
> Some comments:

1. The first section is specific to ubuntu - xubuntu, kubuntu, lubuntu users will not have nautilus installed. Its also possible that installing nautilus-terminal will also install nautilus (unable to verify) which might cause problems on some (ie. xubuntu). Perhaps specifying that these instructions are for ubuntu only or adding similar instructions for the other spins.
...
I agree that the section mentioned by Toz be modified to make it more "agnostic".

---

### Post by vasa1 on 2012-07-06
One more request ...
It's not really specific to the wiki, but a short explanation of "playlist" would be nice.

---

### Post by shantiq on 2012-07-07
thanx guys for feedback

will look at these other softwares i have not encountered previously

moc mpg321 etc    and see how they compare:KS



===================

Vasa    

As regards creating a playlist

go into your Music folder   right-click on any music file **OR** folders

/copy/ paste into a text editor   &   save as playlist.m3u

then play that playlist    ```
 nvlc playlist.m3u
```

```
 mplayer playlist.m3u
```

also you can add internet radio stations   like    ie ```
http://207.200.96.228:8078/
```


**all you need to do from now on is to modify playlist when you wish to and start in same way each time**



my current one looks thus

```
http://207.200.96.228:8078/

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Sync24 - Comfortable Void (FLAC)/Sync24 - Comfortable Void.cue


/home/shantiq/.aMule/Incoming/Netzwerk - 1995 - Memories.wv

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/The Flamin' Groovies - 1971 - Teenage Head [Castle DOJOCD58][NL+]/The Flamin' Groovies - 1971 - Teenage Head.wv.cue

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Flamin Groovies - Flamingo/CDImage(flac).cue

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Henry Cow - In Praise Of Learning (1975) [FLAC]/In Praise of Learning.cue

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Rozalla - Everybody's Free-Style 1993 (Remixed To Perfection) [1993]/01. Rozalla - Everybody's Free (Source Remix).flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Rozalla - Everybody's Free-Style 1993 (Remixed To Perfection) [1993]/02. Rozalla - Believe In Yourself (Rapinos Transylvanian Sunset Mix).flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Rozalla - Everybody's Free-Style 1993 (Remixed To Perfection) [1993]/03. Rozalla - Born To Love Ya (Havana Mix).flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Rozalla - Everybody's Free-Style 1993 (Remixed To Perfection) [1993]/04. Rozalla - Love Breakdown (Stones Club Mix).flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Rozalla - Everybody's Free-Style 1993 (Remixed To Perfection) [1993]/05. Rozalla - You & Me (Project Reese Mix).flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Rozalla - Everybody's Free-Style 1993 (Remixed To Perfection) [1993]/06. Rozalla - Are You Ready To Fly (Phil Kelsey Remix).flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Rozalla - Everybody's Free-Style 1993 (Remixed To Perfection) [1993]/07. Rozalla - Dont't Play With Me (Development Corporation Mix).flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Rozalla - Everybody's Free-Style 1993 (Remixed To Perfection) [1993]/08. Rozalla - Faith (Tomahawak Mix).flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Rozalla - Everybody's Free-Style 1993 (Remixed To Perfection) [1993]/10. Rozalla - Faith (Dubmental).flac


/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/LP_Genesis_1973_Live/genesis_live.cue

/home/shantiq/Route des Festivals - Radio France 8958.mp3


/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/VA - Nuggets - Original Artyfacts from the First Psychedelic Era, 1965-1968 (Rhino Box Set)


/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Thinking Plague - Decline And Fall.cue

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Alio Die & Martina Galvagni - Eleusian Lullaby [2008,Projekt]/Alio Die & Martina Galvagni - Eleusian Lullaby.cue
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Discipline - To Shatter All Accord.Soria/Discipline - To Shatter All Accord.ape.cue

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Los Papines - Rumba sin Alarde (1994, El Inspector de la Salsa) [eac-flac-scans] byDrBull/Los Papines - Rumba sin alarde.cue





/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Flamin' Groovies - 1976 Shake Some Action/CDImage.ape.cue



/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/01 - Happenings Ten Years Time Ago.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/02 - Good Vibrations.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/03 - Rain.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/04 - Most Likely You Go Your Way And I'll Go Mine.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/05 - If Six Was Nine.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/06 - Strawberry Fields Forever.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/07 - Black And White.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/08 - Love Of The Common Man.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/09 - When I Pray.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/10 - Cliché.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/11 - The Verb 'To Love'.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Faithful/12 - Hamburger Hell.flac

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/World_on_3_-_Samba_Mapangala_in_session_b01kgk70_default.m4a
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Punk_Rock_USA_-_Episode_1_b00z2pmd_default.m4a
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Punk_Rock_USA_-_Episode_2_b00z6b3v_default.m4a
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Flamin'_Groovies_-_Yesterday's_Numbers-qIgB5Hmkugc.mp3
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Punk_Rock_USA_-_Episode_3_b00z6b3x_default.m4a
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Punk_Rock_USA_-_Episode_4_b00z701z_default.m4a


/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Natalie_Merchant_Live_in_Concert_16_9-HqP6bNRxFdk.mp3
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Rogsam Swings, C.K. Mann - Salsa con Gana! (1996, Rogsam) [eac-flac-scans] byDrBull/Salsa con Gana.cue

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Todd Rundgren - Hermit Of Mink Hollow (1978)[1996]/Hermit Of Mink Hollow.cue




/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Can - 2012 - The Lost Tapes (3 CD) [Mute, 62957] FLAC/CD 3/The Lost Tapes CD3.cue
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Machiavel - Jester.Soria/Machiavel - Jester.ape.cue

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/can - canobits/CD 1
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/can - canobits/CD 2
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/can - canobits/CD 3

# persian
http://213.73.255.244:10700
http://lyd.nrk.no:80/nrk_radio_klassisk_mp3_h
http://bbcmedia.ic.llnwd.net/stream/bbcmedia_lc1_radio3_p?s=1340361052&e=1340375452&h=882a40f197043f1e8e26598ffc59b650




/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Burnt Friedman & Jaki Liebezeit - Secret Rhythms 4 (2011)/01 204-07.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Burnt Friedman & Jaki Liebezeit - Secret Rhythms 4 (2011)/02 128-05.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Burnt Friedman & Jaki Liebezeit - Secret Rhythms 4 (2011)/03 182-11.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Burnt Friedman & Jaki Liebezeit - Secret Rhythms 4 (2011)/04 131-07.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Burnt Friedman & Jaki Liebezeit - Secret Rhythms 4 (2011)/05 120-11.flac
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Burnt Friedman & Jaki Liebezeit - Secret Rhythms 4 (2011)/06 120-05.flac


/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/00- Habanot_Nechama_Berlin_2012.zip
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/VA - Charangas en Cuba (2000, Salsa Center - EGREM) [eac-flac-scans] byDrBull/Charangas En Cuba.cue
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Medina Azahara-1979 - Paseando por la Mezquita/MEDINA AZAHARA - Paseando por la Mezquita.cue

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Can - 2012 - The Lost Tapes (3 CD) [Mute, 62957] FLAC/CD 1/The Lost Tapes - CD 1.cue
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Can - 2012 - The Lost Tapes (3 CD) [Mute, 62957] FLAC/CD 2/The Lost Tapes - CD 2.cue
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/The Beatles - Magical Mystery Tour
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Burnt Friedman; Jaki Liebezeit - (2002) Secret Rhythms, Vol. 1/Burnt Friedman; Jaki Liebezeit - Secret Rhythms, Vol. 1.cue




/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Fairuz - Ya Tara Nessina (flac)
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/John Martyn - Glorious Fool [1981] EAC Flac Log Cue
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/luca santtana
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Budhaditya Mukherjee - Ahir Bhairav, Puriya


/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Emily_Kokal_of_Warpaint_-_Troubled_Waters_Duke_Ellington-8YDzfMkW8WE.mp3
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Emily_Kokal_Warpaint_-_Untitled_The_Echo_Los_Angeles_CA_5_2_12-V8UtPtJ_DVo.mp3
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Emily_Kokal_Warpaint_-_Him_The_Echo_Los_Angeles_CA_5_2_12-B0FgOIjKuYM.mp3
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Emily_Kokal_Dilettante_-_February_8th_2012-eIgziv8GSIU.mp3
/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/00- Habanot_Nechama_Berlin_2012.zip

/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music/Angus MacLise
```





wow moc is excellent in its layout will add it straightaway     thanx for the info

not better [sound much muted compared to nvlc/mplayer but certainly another route that can be used/   is there a way to change the blue-grey color or is it the only one?

colors can really enhance a program [ATTACH]220810[/ATTACH]

---

### Post by sysaxed on 2012-07-07
> **shantiq said:**
> 
not better [sound much muted compared to nvlc/mplayer but certainly another route that can be used/   is there a way to change the blue-grey color or is it the only one?

Was it about moc?
If yes, then you can change themes by pressing T (case sensitive). (looks like this key is not even documented, found it by accident)
You can even create custom themes. All themes are stored here /usr/share/moc/themes (manual said, that they should be in ~/.moc/themes , but that's not true)
The problem is that I'm unable to find a way to make it persist. Every time I restart moc it returns to default theme... 
There's a way to change config file but I can't even find it.

Sound volume is okay on my machines.
Maybe you change software mixer in moc?
Try pressing x a few times to change the current mixer or you can try pressing w to disable software one.

---

### Post by sysaxed on 2012-07-07
ALRIGHT! Got it working.

So you create a new file in /home/yourusername/.moc called "config"
Now add this line to your config file(for example):
```
Theme = /usr/share/moc/themes/darkdot_theme



```Please don't forget to end your config file with a newline, otherwise you'll see this error
```
FATAL_ERROR: Parse error at the end of the config file (need end of line?)!
```Now change permissions of your config file, otherwise you'll get this error:
```
FATAL_ERROR: Configuration file is not secure: /home/alex/.moc/config
```By default I had
Owner: read and write
Group: read and write
Other: read only
not executable

Changing group from "read and write" to "read only" fixed this problem.

I was looking for other options and found some guy who posted his config file here:
[http://dotfiles.org/~chillu/.moc/config]("http://dotfiles.org/%7Echillu/.moc/config")[U][URL="http://dotfiles.org/%7Echillu/.moc/config"]

[/URL][/U] And here is some nice article [http://blog.jwcxz.com/?p=547](http://blog.jwcxz.com/?p=547)[URL="http://dotfiles.org/%7Echillu/.moc/config"]

[/URL]By the way, when installing moc you might want to install moc-ffmpeg-plugin too for playing other file formats.

---

### Post by vasa1 on 2012-07-07
> **shantiq said:**
> ...
Vasa    

As regards creating a playlist

go into your Music folder   right-click on any music file **OR** folders

/copy/ paste into a text editor   &   save as playlist.m3u

then play that playlist    ...
Done. And thank you :)

---

### Post by andrew.46 on 2012-07-26
> **Toz said:**
>  My understanding is that mpg123 is non-free (in that you can't distribute the code) whereas mpg321 is the opensource version.

I believe there is no licensing problem with Thomas Orgis's work with mpg123, license problems were with an older version. But I have been wrong before :).

---

### Post by shantiq on 2012-07-26
> **sysaxed said:**
> Was it about moc?
If yes, then you can change themes by pressing T (case sensitive).



thanx   man sorry just saw that today had not visited here for a while

thanx for all spot-on detailed info:KS    black and white and i am happy again:KS    and yes as good as nvlc::]]      cuefiles not recognized tho   but navigation is a dream   ;   really well designed   [added ffmpeg plugin as advised]


sound is ok now   dont know what it was when i last tried it

[CENTER][ATTACH]221841[/ATTACH][/CENTER]


**PS**    on reloading found that to set the new theme manually did not stick

so  had to use this to make it stick  > sudo chmod 755 /home/yourusername/.moc/config

---

### Post by sysaxed on 2012-07-28
Oh, by the way!
Default moc config file is located here
/usr/share/doc/moc/examples/config.example.gz

And this is wrong:
```
 sudo chmod 755 /home/yourusername/.moc/config 
```

And this is correct(config file doesn't have to be executable)

```
 sudo chmod 644 /home/yourusername/.moc/config 
```

---

### Post by shantiq on 2012-07-28
i  see.    but does it matter if it is made executable?

wasnt sure so picked that instead of not


what is the difference?

---

### Post by sysaxed on 2012-07-28
> **shantiq said:**
> i  see.    but does it matter if it is made executable?

wasnt sure so picked that instead of not

what is the difference?

It simply does not need to be executable, it's not a script, it's a config file.
My approach gives minimal needed permissions to a file.

---

### Post by shantiq on 2012-10-09
added this [**route**]("https://help.ubuntu.com/community/PlayMusicFromCommandLine") with ffplay too   [thanx to info nothingspecial gave me]


cd to Music folder then


> 

 for i in */
 do
 cd "$i"
 for f in nocaseglob nullglob *.{flac,ape,wv,m4a,aac,mp4,mp3,shn,wma,tta} ; do ffplay -nodisp -autoexit "$f"; done
 cd ..
 done


set up a [**full player**]("http://ubuntuforums.org/showpost.php?p=12287721&postcount=6")

---

