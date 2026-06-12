---
title: "WMII and ruby config problems"
date: 2006-10-10
forum: Desktop Environments
---

### Post by Wind_Sp00n on 2006-10-10
I cannot seem to get wmii to recognize the new wmiirc file in place, because I should of been greeted by a message when I start wmii, or had the ability to view the message by pressing alt-a.

[http://www.ubuntuforums.org/showthread.php?t=203080](http://www.ubuntuforums.org/showthread.php?t=203080)
The link above is the link I used to try to get wmii-ruby to work, but I will elaborate on how

To begin with, I compiled wmii from the source that they provided on the wmii website. (I used wmii 3.1, not the dev. package) Then I decided to use the default configs, so I went to their site and downloaded the ruby wmii 3.1, ran "ruby install.rb" and went into the wmii environment. There was no 'config-help' available.

Then I looked at the guide again. I decided to use the binary compiled for dapper this time. I removed the previous installation of wmii and installed the binary and followed the steps again. (The binary version was 3.1, and the ruby wmii was 3.1) And still I have nothing.

Another thing that indicates that wmii is not understanding the new wmiirc file is that it should of auto generated a wmiirc-config.rb file. I did try on both versions to copy the sections of the wmiirc that indicated that the wmii configuration code was there, and made my own wmiirc-config file. With the new wmiirc-config file, I Proceeded to edit one color value to be black, which never showed up on either focused or non focused windows.

Im greatly confused as to what im doing wrong here. Am I missing a essential file for wmii to use ruby? (I did do an apt-get install ruby, which is how I was able to run 'ruby install.rb') is the wmiirc file simply written wrong, or is there a section that I need to edit? (Although I believe that I shouldn't edit the file, because it states on the file that editing it would not be a good idea, not that I would want to edit it, seeing as I cant comprehend what is going on.)


SOLUTION: make sure the wmiirc script located in ~/.wmii-3 is executable!
use chmod +x ~/.wmii-3/wmiirc to make it executable.

---

