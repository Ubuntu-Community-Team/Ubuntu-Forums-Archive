---
title: "Videos"
date: 2009-04-02
forum: General Help
---

### Post by cowboy7305 on 2009-04-02
have no idea if this can be done but i want to find out if you can copy videos to dvd ,i have a lot of old movies and would like to copy them over ,what hardware do i need and also software and can it be done using Ubuntu 8.1 full install
Many thanks

---

### Post by taurus on 2009-04-02
What format are those old videos?  You can use devede (in the repos) to convert .avi to DVD format before you burn it to a DVD so it would play on a stand alone DVD player.

---

### Post by philinux on 2009-04-02
Once converted or not, there's a burner installed by default.

Brasero. Apps>Sound & Video menu.

---

### Post by cowboy7305 on 2009-04-02
as far as i know thy are VCR 
i need to know if there is hardware out there that i can use to put movies onto computer  so i can convert to Dvd

---

### Post by mb_webguy on 2009-04-02
You'll need a [video capture card]("http://www.mythtv.org/wiki/Video_capture_card"), if you don't have one already, with inputs compatible with the outputs of your VCR (i.e. coaxial cable, component a/v, etc.).

Plug your VCR into the video capture card, then play the video on your VCR and enter the following command in the terminal to capture the video on your computer.```
cat /dev/video0 > /path/to/filename.mpg
```Of course, "video0" should be changed to the device corresponding to your video card, and you should substitute the actual location of the output file for "/path/to/filename.mpg".  Hit Ctrl+C to stop capturing video.

If you're recording a long video and want to stop capturing at a certain time, you can use the "at" command.  So if it's 4:00pm, and you want to capture video for two hours, you could use the following command.```
cat /dev/video0 > /path/to/filename.mpg &
at 6:00pm
at> killall cat
```The "&" runs the command in the background, allowing you to enter subsequent commands.

Once you've captured the video to an mpg, you'll probably want to use Avidemux or something similar to crop unwanted static and black frames from the beginning and ending.  You can then use something like DeVeDe, ManDVD, or DVD Styler to create a nice DVD complete with menus.  Many current DVD players can play DivX DVDs, so you could alternatively use Handbrake or Avidemux to convert the video to an xvid/mp3 avi, and then burn multiple movies to a data DVD using Brasero or k3b.

---

