---
title: "Xbox360 / fuppes / libtag / ffmpeg stream problems"
date: 2007-11-08
forum: Gaming &amp; Leisure
---

### Post by mark_vinton on 2007-11-08
hey, i'm having quite a time getting everything *perfect* on my xbox stream situation.  using anonymous coward's advice things are going pretty well, but i have two problems as follows:

first, i cannot seem to enable taglib and therefore make the xbox see the song metadata, nothing but my audio files.  it's set to "enable" under my fuppes.cfg but when i open the http interface it says it's not enabled.  

second problem- .mov files with 5.1 audio don't work- that's ok because i just transcoded them to .asf files w/ a/52 stereo, and fuppes/ffmpeg -should- transcode and stream them.  however, when i rebuild the database with fuppes it WILL NOT find the new files i have created in my shared directory. 

any ideas?  i'm at my wit's end on these problems.  thanks.

---

### Post by mark_vinton on 2007-11-09
bump

---

### Post by Octagonal on 2007-11-10
I don't know about the first problem.  
I installed Fuppes according to the wiki here:
[http://fuppes.ulrich-voelkel.de/wiki/index.php/Microsoft_Xbox_360](http://fuppes.ulrich-voelkel.de/wiki/index.php/Microsoft_Xbox_360)
and it all seemed to work for me including taglib being enabled.

As far as I know the xbox 360 does not support .asf file extensions but it does support the container--I'm thinking if you just renamed the .asf files to .wmv it should work.

Here's what I use to convert to mp4 or wmv:
#mp4
ffmpeg -y -i "inputmovie.mkv" -f mp4 -title "titleofmovie" -vcodec libx264 -level 41 -b 5120k -bt 5120k -bufsize 14000k -maxrate 14000k -g 300 -coder 1 -acodec libfaac -ac 2 -ar 44100 -threads 2 -r 23.976 "outputmovie.mp4"

#wmv
ffmpeg -y -i "inputmovie.avi" -vcodec wmv2 -sameq -acodec wmav2 -ac 2 -ab 192000 -ar 44100 "outputmovie.wmv"

---

### Post by mark_vinton on 2007-11-11
hey thanks for the advice, i'm gonna give it a shot.  the metadata issues i've had are sort of resolved.  now it has all sorts of pretty album, artist, genre folders etc, but it lists each mp3/m4a twice and will play neither.  that's no biggie b/c i have a nice long coax digital cable running from my pc to the stereo and i rarely use the xbox to listen to music. 

however, the video thing will be awesome if i get it figured out.  thanks again for the advice.  i'll let ya know what's shakin.

---

