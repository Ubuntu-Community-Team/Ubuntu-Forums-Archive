---
title: "Trying to Play Oldschool Runescape with Chrome on Ubuntu."
date: 2014-10-08
forum: Gaming &amp; Leisure
---

### Post by tommy15 on 2014-10-08
Okay, I'm not entirely sure what anyone who's reading/willing to help needs in terms of information (and if you are reading right now, thank you so much! Please continue!), so this post might be a bit long. I'll try to keep it organized. I would also like to inform you that I am *not* skilled with computers. I can do really simple things that anyone who read a few guides+spent a couple of years using a computer could do. Linux/Ubuntu (I'm not entirely sure which one is which) is a completely foreign platform for me.

So I have a chromebook. HP Chromebook 14, intel based. I've been wanting to play Runescape lately, specifically Oldschool Runescape, due to nostalgia/need time to kill. Problem is, you can't play Runescape on a chromebook because Java doesn't work on chromebook. I asked reddit for some help first.

Here's the link to my post. [http://www.reddit.com/r/2007scape/comments/2hw1ld/playing_osrs_on_a_chromebook_anyone_got_any_ideas/](http://www.reddit.com/r/2007scape/comments/2hw1ld/playing_osrs_on_a_chromebook_anyone_got_any_ideas/)

Lo and behold, someone from a reddit thread directs me to this link. [http://lifehacker.com/how-to-install-linux-on-a-chromebook-and-unlock-its-ful-509039343](http://lifehacker.com/how-to-install-linux-on-a-chromebook-and-unlock-its-ful-509039343)

So I installed Ubuntu with Crouton, and it was very easy and successful; I have a second desktop, running on Linux/Ubuntu. I thought my worries were over there.

But it's not that simple, of course. First of all, I didn't like the default browser, Netsurf. Maybe I'm dumb and it's incredible, but I just didn't like it that much compared to chrome. But I was willing to stick with it then, I just wanted to play Runescape. But when I went to the website to try playing in browser, nothing showed up. Then I remembered:

I need Java. And I had gotten sick of Netsurf, so installing Google Chrome was going to be my second goal as well.

So I spent some time trying to do both of these things, and with a stroke of luck that I was afraid I'd never see, I got chrome to work through this article:[http://askubuntu.com/questions/79280/how-to-install-chrome-browser-properly-via-command-line](http://askubuntu.com/questions/79280/how-to-install-chrome-browser-properly-via-command-line)

So awesome, I have chrome now. Now, my problem is Java. 

I tried playing Runescape again through the Chrome browser (I don't know, maybe I'll get lucky?) and this time, something showed up. Unfortunately, it was just a message from Runescape telling me to install Java or update it. But hey, progress right? 

But, from what I know, most of stuff installed on Ubuntu has to be done through the command line, right? So Javas links for downloads for Linux weren't going to cut it.

And here's the strange thing: If I type java in my command line, a bunch of information comes up as if Java has been installed. Which I have done, using this link: [https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get](https://www.digitalocean.com/community/tutorials/how-to-install-java-on-ubuntu-with-apt-get)

However, for reasons I can't understand, this still doesn't let me play Runescape, and clicking to play tells me that I don't have Java. So I'm assuming that this has done little to nothing. 

I started hearing a bit about this browser plugin called Icedtea that worked with Chrome, Firefox and some other browser. I assumed that a browser plugin was probably my best and only chance of getting this to work. I asked for help on reddit again, but a subreddit specifically for Ubuntu: [http://www.reddit.com/r/chrubuntu/comments/2ig0gp/getting_the_icedtea_java_plug_in_on_my_chrome_in/](http://www.reddit.com/r/chrubuntu/comments/2ig0gp/getting_the_icedtea_java_plug_in_on_my_chrome_in/)

His advice was very helpful, but for some reason, every time I tried clicking the download button to this link ([https://apps.ubuntu.com/cat/applications/icedtea-plugin/](https://apps.ubuntu.com/cat/applications/icedtea-plugin/)), it would tell me that it "Failed to open URI apt://icedtea-plugin". I have no idea why it's doing this.

I went over to the instructions on the Java site and found a link for "different flavors of Linux" and clicked on Ubuntu. It gave me links to Icedtea, icedtea plugin 6 and 7. Both gave me the same response, but it was changed according to the number. Here's a link to those downloads, scroll down a little bit, it's under OpenJDK: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

So none of these 3 download links are working for me, and I have no idea what to do through the command line; I've tried with a little help and it's yielded no results. Can someone please help me? I've been trying to get this working for about a week now...

Possibly important links, in order of posting:
[http://www.reddit.com/r/2007scape/comments/2hos0d/im_considering_playing_07_runescape_again_but_im/](http://www.reddit.com/r/2007scape/comments/2hos0d/im_considering_playing_07_runescape_again_but_im/)
[http://www.reddit.com/r/2007scape/comments/2hw1ld/playing_osrs_on_a_chromebook_anyone_got_any_ideas/](http://www.reddit.com/r/2007scape/comments/2hw1ld/playing_osrs_on_a_chromebook_anyone_got_any_ideas/)
[http://www.reddit.com/r/chromeos/comments/2i06qn/ive_got_some_issues_with_this_ubuntu_ive/](http://www.reddit.com/r/chromeos/comments/2i06qn/ive_got_some_issues_with_this_ubuntu_ive/)
[http://www.reddit.com/r/2007scape/comments/2i0dzs/im_really_sorry_for_posting_this_much_and_i_swear/](http://www.reddit.com/r/2007scape/comments/2i0dzs/im_really_sorry_for_posting_this_much_and_i_swear/)
[http://www.reddit.com/r/chrubuntu/comments/2ig0gp/getting_the_icedtea_java_plug_in_on_my_chrome_in/](http://www.reddit.com/r/chrubuntu/comments/2ig0gp/getting_the_icedtea_java_plug_in_on_my_chrome_in/)

Thanks so much for reading!

---

### Post by King Dude on 2014-10-08
[http://services.runescape.com/m=rswiki/en/Linux_Native_Clients#The_RuneScape_UNIX_Client_.28RSU_Client.29](http://services.runescape.com/m=rswiki/en/Linux_Native_Clients#The_RuneScape_UNIX_Client_.28RSU_Client.29) 

[OpenJDK]("http://openjdk.java.net/install/") (It's Java but open source)

---

### Post by tommy15 on 2014-10-08
[B][I][U]THANK. YOU. SO. MUCH.

[/U][/I][/B]Everything worked perfectly, and I now have the client and can now play the game! I am so grateful, thank you so much!

---

