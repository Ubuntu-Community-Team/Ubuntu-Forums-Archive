---
title: "DVD Playback. Does. Not. Work."
date: 2009-03-09
forum: General Help
---

### Post by pacificflows on 2009-03-09
I understand there's some jibba-jab that I have to do in the terminal before I can play commercial DVDs with any media playing software.

I have followed a few sets of instructions and gotten mixed results. Basically, I started from the Totem player flat out refusing to play the DVD. Now I get about 5 mins into the movie before I receive an error message accusing me of not having libdvdcss (or something like that) installed. I know for a fact that I DO have that file, or one with a deceptively similar name, installed. It appears as though the media player is just failing to recognize it, but I have no idea.

Please. A simple set of step 1, step 2, etc., instructions that will get me able to do something as simple as play dvds would help very much.

What's the deal with this, anyways? Do microsoft employees make it a habit to sabotage linux programming? Who's *** do I have to kick?!?!

---

### Post by tommcd on 2009-03-09
Are you sure you have libdvdcss installed? How did you install it? You should get the codecs and libdvd stuff from medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just open a terminal (applications > accessories > terminal) and copy and paste the commands listed under "Adding the Repositories".
Then follow "add the GPG Key".
Then "sudo apt-get install libdvdcss2" (without the quotes) in the terminal to install libdvdcss2.

Grab the windows codecs while you are there:
"sudo apt-get install w32codecs" (again, without the quotes)
If you are running 64 bit Ubuntu then get the 64 bit codecs.

These packages are not free (as in freedom) software, so they can't be included with Ubuntu or Microsoft's lawyers would skin us alive.

---

### Post by binbash on 2009-03-09
you also need libdvdnav if you want to play menus with mplayer

---

### Post by 3rdalbum on 2009-03-09
Don't use Totem for DVDs. In three years of using Linux I've never had Totem work for DVD playback. Instead, install VLC. Also check that libdvdcss has been installed from the Medibuntu repository, and you'll be fine.

---

### Post by pacificflows on 2009-03-09
> **3rdalbum said:**
> Don't use Totem for DVDs. In three years of using Linux I've never had Totem work for DVD playback. Instead, install VLC. Also check that libdvdcss has been installed from the Medibuntu repository, and you'll be fine.

VLC does not work at all. It won't even open when I try to use it to play DVDs.

---

### Post by pacificflows on 2009-03-09
> **tommcd said:**
> Are you sure you have libdvdcss installed? How did you install it? You should get the codecs and libdvd stuff from medibuntu:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Just open a terminal (applications > accessories > terminal) and copy and paste the commands listed under "Adding the Repositories".
Then follow "add the GPG Key".
Then "sudo apt-get install libdvdcss2" (without the quotes) in the terminal to install libdvdcss2.

Grab the windows codecs while you are there:
"sudo apt-get install w32codecs" (again, without the quotes)
If you are running 64 bit Ubuntu then get the 64 bit codecs.

These packages are not free (as in freedom) software, so they can't be included with Ubuntu or Microsoft's lawyers would skin us alive.

So it's Microsoft's lawyers who need their asses kicked? I'LL DO IT, MAN!!!

But I installed libdvdcss with the terminal. I'll follow your instructions as closely as I have understood them. Hopefully it will work...

Thank you for the help, everyone.

---

### Post by tommcd on 2009-03-10
Totem does not play DVDs for me either. Mplayer plays DVDs fine for me with libdvdcss installed. Mplayer is still the king of all linux media players. Mplayer wins the linuxquestions.org forums 'members choice awards' year after year for best video player:
[http://www.linuxquestions.org/questions/2008-linuxquestions.org-members-choice-awards-83/video-media-player-application-of-the-year-695638/](http://www.linuxquestions.org/questions/2008-linuxquestions.org-members-choice-awards-83/video-media-player-application-of-the-year-695638/)
VLC was a close second though.
So install Mplayer. **Xine** is very good for playing DVDs also. Just run:
```
sudo apt-get install xine-ui
```
to install it.

---

### Post by LittleCory on 2009-03-10
I always install ubuntu-restricted-extras.  Then I use mplayer.  Works every time.

---

### Post by pacificflows on 2009-03-10
tommcd rolled a 20 on his "help-a-noob" check.

thanks, tom. :D

---

### Post by carml on 2009-03-10
> **pacificflows said:**
> VLC does not work at all. It won't even open when I try to use it to play DVDs.
Did you look at System->Help & support section Music,Video,photographs?

---

