---
title: "How to backup DVD's for playback on computer &amp; iPhone? - iTunes or something else?"
date: 2009-02-11
forum: General Help
---

### Post by PsychedelicWonders on 2009-02-11
How exactly do I back up my DVD's onto my computer so that I can play them back easily on the computer whether it is ubuntu or windows or my iPhone?

Would iTunes be the best route?

People have said you cant backup dvds via itunes... but I thought I backed one up there before?

I want to be able to utilize the DVD and its menus just like normal through my dvd player.

What do you guys suggest?

---

### Post by scouser73 on 2009-02-11
You need to download acidrip which is in the Repos.

---

### Post by RD1 on 2009-02-11
[HANDBRAKE]("http://handbrake.fr/") :P

---

### Post by PsychedelicWonders on 2009-02-11
So what is the difference between those two programs?

Am i better off doing this in Ubuntu, or iTunes/windows?

I want to be able to load these onto my iphone and also view them normally on the computer...

will those two programs rip them in a format that will allow me to do that?

---

### Post by mb_webguy on 2009-02-11
I second Handbrake.  It's reliable, very simple to use, and has presets for various devices including the iPod, iPhone/iPod Touch, PSP, PS3, and Xbox 360.

Videos intended for use for a hand-held device are fairly small, and not what you'd want for viewing on your computer.  (On the other hand, hand-held devices are very specific about the format and size video they will play, so you can't put just any video on them.)  So if you want a good-quality version for your computer and a smaller one that is appropriate for your hand-held device, you'd have rip the DVD twice.

---

### Post by punx45 on 2009-02-11
itunes does nothing with DVDs.   if you want to put videos in your iphone i suggest handbrake, as the iphone is very picky about videos that it will play, and handbrake has working presets for it.   as for keeping the menu structure, that will only be useful on your computer.   you could just copy the video_ts structure to HDD and if you have libdvdcss installed, VLC will be able to play it.   you will need libdvdcss installed for handbrake to rip copy protected dvds anyway.    (i think you should be all set if you have VLC installed)

---

### Post by PsychedelicWonders on 2009-02-13
> **punx45 said:**
> itunes does nothing with DVDs.   if you want to put videos in your iphone i suggest handbrake, as the iphone is very picky about videos that it will play, and handbrake has working presets for it.   as for keeping the menu structure, that will only be useful on your computer.   you could just copy the video_ts structure to HDD and if you have libdvdcss installed, VLC will be able to play it.   you will need libdvdcss installed for handbrake to rip copy protected dvds anyway.    (i think you should be all set if you have VLC installed)


Hmm.  i'm not too familar with going in and finding just the video_ts file and dont know if I have libdvdcss, but know I do have vlc.

I will get this handbrake since I want iPhone compatiblitity.

sucks i will have to rip twice though.

Good thing is I dont have many I want to do this to.

What do I type to get handbrake?

---

### Post by mc4man on 2009-02-13
Other than building HB this will do you fine

[https://launchpad.net/~handbrake-ubuntu/+archive/ppa](https://launchpad.net/~handbrake-ubuntu/+archive/ppa)

---

### Post by PsychedelicWonders on 2009-02-13
> **mc4man said:**
> Other than building HB this will do you fine

[https://launchpad.net/~handbrake-ubuntu/+archive/ppa](https://launchpad.net/~handbrake-ubuntu/+archive/ppa)

What do you mean "other than building HB"?

---

### Post by mc4man on 2009-02-13
> other than building HB"?

Well I don't think handbrake (HB) is available in ubuntu repos, so you could compile (build) it from source or add the ppa and then apt-get it or find it in synaptic

---

### Post by PsychedelicWonders on 2009-02-13
ahh alright nice.

thanks.

Once I get my dsl up later today (hopefully) I will follow that link.

thanks.

---

### Post by mc4man on 2009-02-13
just curious - have you gotten your new box stable yet?

---

### Post by PsychedelicWonders on 2009-02-13
yes and no.

it comes and it goes.

My internet was supposed to be hooked up a week ago, but all mighty ATT cant even acoomplish somethign as easy as that.

I need to fix the video drivers in ubutnu... windows seems to be working fine.

but cant do that until i get the internet.

---

### Post by PsychedelicWonders on 2009-03-21
> **mc4man said:**
> Other than building HB this will do you fine

[https://launchpad.net/~handbrake-ubuntu/+archive/ppa](https://launchpad.net/~handbrake-ubuntu/+archive/ppa)

Ok, internet is back up now finally.

I tool a look at that link and just dont know where to start.

Which one of those packages do I download?

Will this install HB completly, or is this just a part of the "build" you mentioned and I will need to download other "parts"?

I guess I'm just confused?

---

### Post by mb_webguy on 2009-03-22
You generally don't want to download packages from a PPA.  You want to add the PPA to your Software Sources, and then install the software from the PPA in the same way you would software from the Ubuntu repositories.

To add the PPA and install Handbrake:

1) Open System->Administration->Software Sources.

2) On the Third-Party Software tab, click the Add button, and paste the following line in the "APT line:" text box.```
deb http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu intrepid main
```If you're using Hardy (8.04), then replace "intrepid" with "hardy".  Click the "Add Source" button.

3) Right-click [this link]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xE43D207C62D38753") and save the file to your computer.

4) Back in Software Sources, on the Authentication tab, click the "Import Key File" button, select the file you just downloaded, and click "OK".

5) Close the Software Sources window.  You will be prompted to update your sources, so do so.

6) Install Handbrake using Add/Remove Applications, Synaptic Package Manager, or with the command "sudo apt-get install handbrake-gtk" in the terminal.

This may seem like a lot of work just to install a program, but doing so will make sure that you have access to all of the dependencies required by Handbrake which are also in the Handbrake PPA, and will enable you to receive automatic updates for Handbrake through Update Manager as you do for software installed from the official repositories.

---

### Post by PsychedelicWonders on 2009-03-28
> **mb_webguy said:**
> You generally don't want to download packages from a PPA.  You want to add the PPA to your Software Sources, and then install the software from the PPA in the same way you would software from the Ubuntu repositories.

To add the PPA and install Handbrake:

1) Open System->Administration->Software Sources.

2) On the Third-Party Software tab, click the Add button, and paste the following line in the "APT line:" text box.```
deb http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu intrepid main
```If you're using Hardy (8.04), then replace "intrepid" with "hardy".  Click the "Add Source" button.

3) Right-click [this link]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xE43D207C62D38753") and save the file to your computer.

4) Back in Software Sources, on the Authentication tab, click the "Import Key File" button, select the file you just downloaded, and click "OK".

5) Close the Software Sources window.  You will be prompted to update your sources, so do so.

6) Install Handbrake using Add/Remove Applications, Synaptic Package Manager, or with the command "sudo apt-get install handbrake-gtk" in the terminal.

This may seem like a lot of work just to install a program, but doing so will make sure that you have access to all of the dependencies required by Handbrake which are also in the Handbrake PPA, and will enable you to receive automatic updates for Handbrake through Update Manager as you do for software installed from the official repositories.

Ok, I got past step 5 and this is the error message I got:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5

There is a picture attached also.

Is that an issue?  Or is everything still ok?

Can I still go ahead with step 6 and install handbrake via the terminal now?

---

### Post by mb_webguy on 2009-03-29
I think you can still install Handbrake, it will just say it's not authenticated.

I don't know why that method of adding the key didn't work, since I've done it before, but...  Alternatively, you could go into Software Sources, go to the Authentication tab, and remove the key you added.  Then open the terminal and type "sudo apt-get update".  You'll get an error message saying something about a GPG key, which will include a long string of letters and numbers.  Copy that alphanumeric string, and paste it into the following commands for *keyid*.```
gpg --keyserver keyserver.ubuntu.com --recv *keyid*
gpg --export --armor *keyid* | sudo apt-key add -
```When you run "sudo apt-get update" again, you shouldn't get the error message, and packages from the Handbrake PPA won't show up as "not authenticated".

---

### Post by PsychedelicWonders on 2009-04-08
> **mb_webguy said:**
> You'll get an error message saying something about a GPG key, which will include a long string of letters and numbers.  Copy that alphanumeric string, and paste it into the following commands for *keyid*.```
gpg --keyserver keyserver.ubuntu.com --recv *keyid*
gpg --export --armor *keyid* | sudo apt-key add -
```When you run "sudo apt-get update" again, you shouldn't get the error message, and packages from the Handbrake PPA won't show up as "not authenticated".


I suppose I get lost at this part.

I dont understand where the command lines will be/coming from for me to paste the alphanumeric string?

I copy the entire error message and then paste it where?

---

### Post by mb_webguy on 2009-04-08
Ok, you said when you try to update your sources, you get the error:```
W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
```
What you need to copy is the "7D2C7A23BF810CD5" bit.  You actually only need the last 8 digits, but it doesn't matter if you get the whole thing.

Replace the *keyid* in the commands I posted with this key id.  To make it easier on you, just copy and paste the following commands in the terminal:```
gpg --keyserver keyserver.ubuntu.com --recv 7D2C7A23BF810CD5
gpg --export --armor 7D2C7A23BF810CD5 | sudo apt-key add -
```

---

### Post by PsychedelicWonders on 2009-04-13
Am I good?  did it install properly?

I checked under I looked under the main menu and didnt see anything labeled HandBrake?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
psychedelicwonders@JohnnyScience:~$ gpg --keyserver keyserver.ubuntu.com --recv 7D2C7A23BF810CD5
gpg: requesting key BF810CD5 from hkp server keyserver.ubuntu.com
gpg: key BF810CD5: public key "Launchpad PPA for Awn Testing Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
psychedelicwonders@JohnnyScience:~$ gpg --export --armor 7D2C7A23BF810CD5 | sudo apt-key add -
OK
psychedelicwonders@JohnnyScience:~$

---

### Post by mb_webguy on 2009-04-13
Yup.  You did it right.  You shouldn't get those GPG errors anymore when updating (at least for that particular PPA).

---

### Post by PsychedelicWonders on 2009-04-13
> **mb_webguy said:**
> Yup.  You did it right.  You shouldn't get those GPG errors anymore when updating (at least for that particular PPA).

So is handbrake installed now?

Or do I have to go back and try to install it again via the terminal?

youre always on here arent you?  :)

You've been a huge help to me for quite a while now, I really appreciate it.

---

### Post by PsychedelicWonders on 2009-04-13
Ok I ran sudo apt-get update again

Now what code do I do to install handbrake?

---

### Post by mb_webguy on 2009-04-13
Assuming you've added the Handbrake PPA, you can install Handbrake from Add/Remove Applications, Synaptic, or in the terminal using the command "sudo apt-get install handbrake-gtk".

---

### Post by PsychedelicWonders on 2009-04-14
> **mb_webguy said:**
> Assuming you've added the Handbrake PPA, you can install Handbrake from Add/Remove Applications, Synaptic, or in the terminal using the command "sudo apt-get install handbrake-gtk".

I dont even know what the Handbrake PPA is, so I dont know when I would have done it.

How can I tell if I have?

Or should I just run that code in the terminal?

---

### Post by mb_webguy on 2009-04-14
Assuming you followed all of the steps in this post earlier in the thread, then you added the Handbrake PPA.  You can double-check this by opening System->Administration->Software Sources, and looking on the Third-Party Software tab.  If you see a line that starts "http://ppa.launchpad.net/handbrake-ubuntu" then you're right on track.  Just use one of the methods in my most recent post (Add/Remove, Synaptic, or "sudo apt-get install handbrake-gtk") to install Handbrake.

As I may have said before, all of this might have seemed like a lot of work just to install a piece of software, but by adding the repository to your Software Sources, you'll receive automatic updates and upgrades as they're released.

---

### Post by PsychedelicWonders on 2009-04-14
Ok nice, it is installed, thanks.

Now is this easy to use?

Can I just set the preferences on this from the begining and have it rip the DVD once and rip it so that I can view it in either Ubuntu, XP Pro & Vista & on the iPhone?

Kind of a "set it and forget it deal"?

I see all kinds of stuff, cropping, scaling picture clean up etc.

I dont know what any of that stuff is, will I need to if I'm just trying to rip the DVD as is?

---

### Post by mb_webguy on 2009-04-14
You don't have to worry about all of the options unless you really want to.  Here's the easy way to rip a DVD using Handbrake.

Step 1) Click the Source button in the top left, and navigate to the DVD.  Make sure the "Open VIDEO_TS folder" box at the bottom left is checked.  Click Open.

Step 2) Select a preset in the right pane.  Basic->Normal is a good choice for viewing on your computer.

Step 3) Click Start.

That's it.  All you have to do now is sit back and let it do its job.  Depending on your hardware, it might take a while.

Now for a bit more detail...

Presets only set a bunch of different options at once.  You can change specific options after picking a preset.  The default presets tend to use bitrate for the Quality setting -- and that *will* give you a pretty good quality movie, if a very large one -- but most of the time people use a target file size rather than a target bitrate.  A good rule of thumb is 350MB per hour of video.  So for most movies, you will probably want to change Video->Quality to use Target Size instead of Bitrate, and set it to 700.  I also like to click the "2-Pass Encoding" and "Turbo First Pass" boxes under Video->Encoding in order to get a slightly better quality video at the expense of a little bit of extra encoding time.

Also, most of the presets use some form of mp4 for the container.  If you want to play your movies on a DivX-capable DVD player, you will want to create your own preset.  To do this, select "AVI" for the container, "MPEG-4 (XviD)" as the video codec, Target Size of 700 for Quality,  "MP3 (Lame)" as the audio codec, and "Autoselect" for Subtitles (and make sure "Allow only forced subtitles" is checked).  The last bit will hard-code any forced subtitles, such as when characters are speaking in Chinese in an otherwise English-language film.  Now click the plus ("+") button at the bottom of the Preset pane.  Call it something like "DivX-compatible (700MB)".  This will add these settings as a preset, so you don't ever have to manually set them again.

Basically, Handbrake can rip a DVD or convert a DVD in three easy steps, but also offers a lot of options *if you need them*.  You don't have to play around with those extra options if you don't want to do so, as the presets are generally good enough for most purposes.

---

### Post by MeKino on 2009-04-14
Hi,

Thanks for this so far...

But - when I try to import the Key File using Software Sources the GUI crashes.

Any idea how to get round this?

Kino

---

### Post by MeKino on 2009-04-14
OK

For what it's worth, I used Synaptic to load the following:

handbrake-cli_0.9.3+repack1-0ubuntu0~8.04jdong4_i386.deb
handbrake-common_0.9.3+repack1-0ubuntu0~8.04jdong4_all.deb
handbrake-gtk_0.9.3+repack1-0ubuntu0~8.04jdong4_i386.deb

then in the terminal type ghb

handbrake then appears!

---

### Post by mb_webguy on 2009-04-14
> **MeKino said:**
> Hi,

Thanks for this so far...

But - when I try to import the Key File using Software Sources the GUI crashes.

Any idea how to get round this?

Kino

Adding the GPG key using the Software Sources GUI is a bit awkward, in my opinion, and I find using the terminal commands to be easier.  Once you add the PPA, just run "sudo apt-get update" in the terminal.  You'll get one or more GPG key errors, which include a long alphanumeric string.  Copy that string, and paste it into the following commands in place of *keyid*.```
gpg --keyserver keyserver.ubuntu.com --recv *keyid*
gpg --export --armor *keyid* | sudo apt-key add -
```

---

### Post by Slim Odds on 2009-04-14
> **PsychedelicWonders said:**
> sucks i will have to rip twice though.

You don't have to rip it twice. You have to re-encode it two times for the two output formats that you want.

---

### Post by mb_webguy on 2009-04-14
> **Slim Odds said:**
> You don't have to rip it twice. You have to re-encode it two times for the two output formats that you want.

It would take essentially the same amount of time to rip it a second time as it would to transcode the rip to a different format, and would result in better video quality on the second video.

But yes, if you don't have the original DVD handy when you want to create the video for your iPod or other portable media device, you can use the first rip as the source and convert it to the new format.

---

### Post by Slim Odds on 2009-04-14
> **mb_webguy said:**
> It would take essentially the same amount of time to rip it a second time as it would to transcode the rip to a different format, and would result in better video quality on the second video.

Absolutely false on both counts.

1) Ripping a second time means wasting all of that time.

2) The original rip is an EXACT digital copy. There is no quality loss.

You rip once to get an EXACT copy. Then you transcode from that to each target.

---

### Post by speed32219 on 2009-04-14
So if I do not have a WM, can I use HB using the CLI?  If so, where would I get the explanation of the SW switches (Cmd string) to set for the rip I wanted.  

Thx

---

### Post by PsychedelicWonders on 2009-04-14
So I rip once and then do this transcode for every format I want?

i.e. iPhone computer etc?

Can I rip the original DVD in "tv" format?  Already rated for my 46" samsung, or do I have to rip it first in "computer" format and then transcode over to "tv" format?

---

### Post by mb_webguy on 2009-04-14
> **Slim Odds said:**
> Absolutely false on both counts.

1) Ripping a second time means wasting all of that time.

2) The original rip is an EXACT digital copy. There is no quality loss.

You rip once to get an EXACT copy. Then you transcode from that to each target.

If you're ripping an exact copy, why are you using Handbrake?  Just copy the VIDEO_TS directory to your hard drive, or make an ISO with Brasero or k3b.

If you're using Handbrake, you're *not* getting an exact copy, since none of the video codecs supported by Handbrake (h.264, XviD mpeg-4, ffmpeg MPEG-4, and Theora) are lossless.

> **PsychedelicWonders said:**
> So I rip once and then do this transcode for every format I want?

i.e. iPhone computer etc?

Can I rip the original DVD in "tv" format?  Already rated for my 46" samsung, or do I have to rip it first in "computer" format and then transcode over to "tv" format?

There really isn't a "computer" format and a "tv" format.  Unless you use Handbrake to convert the video for a specific device with a small screen like an iPod, the video produced by Handbrake is going to be the same resolution as the source video.  The difference between the different presets has more to do with compatibility with playback devices than quality.  If you're hooking your computer up to your TV, then it doesn't matter what format it's in as long as it's playable on your computer.  If you're planning on playing it using a DivX-compatible DVD player, then it needs to use the audio and video codecs the player can read, but again the resolution isn't changed.

---

### Post by Slim Odds on 2009-04-14
> **mb_webguy said:**
> If you're ripping an exact copy, why are you using Handbrake?  Just copy the VIDEO_TS directory to your hard drive, or make an ISO with Brasero or k3b.

Handbrake can take a VIDEO_TS directory. So you can rip with something else to create that. Then, you can encode multiple times (once for each target format).

---

### Post by mb_webguy on 2009-04-14
Slim, I think we're on different pages here.  The last few dozen posts in the thread have been about using Handbrake to rip a DVD.  Sure, you can make an ISO of the DVD or copy the VIDEO_TS folder, but then you'd have a 4-9GB file or directory on your hard drive, which for most people isn't a viable option.  

And besides, we're talking about *ripping* a DVD, not copying it.  When people talk about ripping a CD, they don't usually mean making an ISO of the CD or simply copying the files from it -- they're talking about converting the songs on the disc to mp3 or ogg files.  The same applies to DVDs.  Ripping a DVD implies converting the DVD video to a more portable format.  That's what Handbrake does, and what copying the VIDEO_TS directory to your hard drive *doesn't*.

---

### Post by Slim Odds on 2009-04-14
> **mb_webguy said:**
> Slim, I think we're on different pages here.
Maybe so...

The title of this post is: How to backup DVD's for playback on computer & iPhone.....

My point was that there is a better way to that than reripping a DVD multiple times.

> ...Sure, you can make an ISO of the DVD or copy the VIDEO_TS folder, but then you'd have a 4-9GB file or directory on your hard drive, which for most people isn't a viable option.For most people???  I disagree, most people have pretty big hard drives these days. Especially if they are ripping stuff for an iPhone, etc. ($$$)

> And besides, we're talking about *ripping* a DVD, not copying it.From wikipedia: **Ripping** is the process of copying audio or video content to a [hard disk]("http://en.wikipedia.org/wiki/Hard_disk"), typically from [removable media]("http://en.wikipedia.org/wiki/Removable_media") or [media streams]("http://en.wikipedia.org/wiki/Streaming_media"). [http://en.wikipedia.org/wiki/Ripping](http://en.wikipedia.org/wiki/Ripping)

Ripping is just copying....

> When people talk about ripping a CD, they don't usually mean making an ISO of the CD or simply copying the files from it -- they're talking about converting the songs on the disc to mp3 or ogg files.Converting songs from a CD (which are small and individual) is a lot different.

> The same applies to DVDs.Pretty different.

---

### Post by mb_webguy on 2009-04-15
> **Slim Odds said:**
> For most people???  I disagree, most people have pretty big hard drives these days. Especially if they are ripping stuff for an iPhone, etc. ($$$)

Hey, if you have a few terabytes of extra storage space, I'll gladly go re-"rip" all of my various videos as exact copies let you host them for me.  Because that's easily what it would take to hold the 300GB or so of movies, television series, and other videos I have ripped to my various hard drives.  If we assume that 300GB consists entirely of DVD movies ripped to 700MB files, and also assume that each of those DVDs were only a DVD-5 (4.7GB), then it would take just over 2TB to store those same videos as ISOs or VIDEO_TS directories.

I don't have nearly as many videos saved to hard drive as many of my friends.  And I know very few people who have several TB of storage.

---

### Post by Jimmynemo2 on 2009-04-15
Just a side note- for anyone else reading this later in particular- thats a lot of hassle to install handbrake- they post .debs on the official handbrake site, so feel free to download it from there for ease of use.

---

### Post by Slim Odds on 2009-04-15
> **mb_webguy said:**
> Hey, if you have a few terabytes of extra storage space, I'll gladly go re-"rip" all of my various videos as exact copies let you host them for me.  Because that's easily what it would take to hold the 300GB or so of movies, television series, and other videos I have ripped to my various hard drives.  If we assume that 300GB consists entirely of DVD movies ripped to 700MB files, and also assume that each of those DVDs were only a DVD-5 (4.7GB), then it would take just over 2TB to store those same videos as ISOs or VIDEO_TS directories.

Man, you don't need to rip every DVD on the planet to encode ONE.

You only need space for ONE. You rip it ONCE, encode 2 or 3 times for the targets that you're interested in and then DELETE IT.

Is this complicated? I don't think so.

---

### Post by mb_webguy on 2009-04-15
> **Slim Odds said:**
> Man, you don't need to rip every DVD on the planet to encode ONE.

You only need space for ONE. You rip it ONCE, encode 2 or 3 times for the targets that you're interested in and then DELETE IT.

Is this complicated? I don't think so.

Ah...  I see what you're saying now.  From your previous post it sounded like you were suggesting that people rip exact copies to their hard drives *permanently* so as to not lose quality, rather than temporarily to make transcoding slightly faster.  I don't really notice a difference when ripping from a disc or an ISO -- the actual transcoding takes the lion's share of the time -- but yeah, reading from the hard drive is much faster than reading from a disc, so it should make transcoding slightly faster.  (Of course, you have to wait the extra minute or so it takes to copy the disc in the first place...)

I still don't consider copying the same as ripping, but I see what you were getting at now.  I can see how it might make the ripping process faster.  Hakuna matata.

---

### Post by PsychedelicWonders on 2009-04-16
Hmm.  I guess I'm confused because this is just a new area to me.

So if I want to make all of my movies digital for play back via my computer on either 19" or 46" LCDs or on an iPhone:

I need to rip this on my HDD via handbrake, transcode to an iPhone format and another format and then delete the original ripped file/dvd?

---

### Post by mb_webguy on 2009-04-17
> **PsychedelicWonders said:**
> Hmm.  I guess I'm confused because this is just a new area to me.

So if I want to make all of my movies digital for play back via my computer on either 19" or 46" LCDs or on an iPhone:

I need to rip this on my HDD via handbrake, transcode to an iPhone format and another format and then delete the original ripped file/dvd?

Not exactly.  Sorry if the side discussion between Slim and me got you a bit confused.

A DVD movie is already a digital format.  It's just stored on the disc in a format that uses very low compression.  As Slim was saying, you *could* simply copy the VIDEO_TS folder from the DVD onto your computer, and play it from there.  OR you could make an ISO of the DVD, which is an image of the disc -- essentially an exact electronic copy of the disc.  Both of these methods, however, will take up about 4-9GB of hard drive space, depending on the disc.

While you could play the movie from a VIDEO_TS directory or ISO file from your computer, you can't play it on other devices.  And as I said, it will take up a lot of room.  The point of using Handbrake is to transcode ("convert") the movie to a different format that uses higher compression (which reduces the size to something more manageable) and that is compatible with the device(s) with which you want to play the movie.  As far as your computer is concerned, the first part is the more important.  But when it comes to things like an iPod or a DivX-compatible DVD player, the latter is the more important, because they only play a limited number of formats.

What Slim was suggesting was that you copy the disc to your computer as the VIDEO_TS folder or an ISO, and then use that as the source for Handbrake.  This has the advantage of not having to have the disc in your drive the whole time, and also may provide a small speed boost since reading from your hard drive is much faster than reading from a disc.

Whether or not you choose to do this or not, you would still need to transcode the movie with Handbrake twice if you want a good-quality version to keep on your computer and another that's playable on your iPod.  You wouldn't want to just transcode it once for your iPod and then watch that video on your computer (even though you certainly *could*), because the screen resolution of the iPod is relatively low, and when the video is transcoded for the iPod the resolution is changed to fit its screen.  So the iPod video will be a lower resolution and lesser quality than the original movie.  And unless you have huge amounts of unused hard drive space, you'll want a more compressed version of the movie to keep on your computer than the VIDEO_TS directory or an ISO.

---

### Post by PsychedelicWonders on 2009-04-17
Ahh ok.
 
now let me ask this.
 
So when I use handbrake for the initial rip, does it rip & then transcode to be comptible with the computer?
 
And then only requiring me to transcode the same file that was already ripped the 1st time via handbrake to a format compatible with my iPhone?
 
Or do I rip with handbrake first, then transcode for computer, transcode for iphone & delete original rip I did with handbrake?

---

### Post by mb_webguy on 2009-04-17
> **PsychedelicWonders said:**
> Ahh ok.
 
now let me ask this.
 
So when I use handbrake for the initial rip, does it rip & then transcode to be comptible with the computer?
 
And then only requiring me to transcode the same file that was already ripped the 1st time via handbrake to a format compatible with my iPhone?
 
Or do I rip with handbrake first, then transcode for computer, transcode for iphone & delete original rip I did with handbrake?

When you rip a DVD with Handbrake, you select the format you want the resulting video to be.  So if you want an avi file with Xvid video encoding and mp3 audio that will be compatible with DivX-compatible DVD players, that's what you tell Handbrake to use when ripping the movie.  If you want an mp4 file with h.264 video encoding and AAC audio, then you would tell Handbrake to use those settings.  And if you want an mp4 with h.264 video and AAC audio resized to be playable on an iPod, then you would tell Handbrake to use *those* settings.  

This is generally handled for you with Handbrake's built-in presets, so all you have to do is pick how the video is to be used from the preset pane, and click Start.

And because you have to determine the format of the resulting video when you rip the DVD, you have to either rip it multiple times for multiple different uses, or else transcode the ripped movie to a different format (which will result in a loss of quality).

---

### Post by PsychedelicWonders on 2009-04-19
> **mb_webguy said:**
> When you rip a DVD with Handbrake, you select the format you want the resulting video to be.  So if you want an avi file with Xvid video encoding and mp3 audio that will be compatible with DivX-compatible DVD players, that's what you tell Handbrake to use when ripping the movie.  If you want an mp4 file with h.264 video encoding and AAC audio, then you would tell Handbrake to use those settings.  And if you want an mp4 with h.264 video and AAC audio resized to be playable on an iPod, then you would tell Handbrake to use *those* settings.  

This is generally handled for you with Handbrake's built-in presets, so all you have to do is pick how the video is to be used from the preset pane, and click Start.

And because you have to determine the format of the resulting video when you rip the DVD, you have to either rip it multiple times for multiple different uses, or else transcode the ripped movie to a different format (which will result in a loss of quality).

Ok, so I will rip once & then transcode for the iPhone.

But what format do I want to rip if I only plan to keep it as a digital copy to play on computer/tv etc?

an avi file with Xvid video encoding and mp3 audio that will be compatible with DivX-compatible DVD players, that's what you tell Handbrake to use when ripping the movie.  If you want an mp4 file with h.264 video encoding and AAC audio, then you would tell Handbrake to use those settings.

---

### Post by Slim Odds on 2009-04-19
> **PsychedelicWonders said:**
> Ok, so I will rip once & then transcode for the iPhone.

But what format do I want to rip if I only plan to keep it as a digital copy to play on computer/tv etc?

an avi file with Xvid video encoding and mp3 audio that will be compatible with DivX-compatible DVD players, that's what you tell Handbrake to use when ripping the movie.  If you want an mp4 file with h.264 video encoding and AAC audio, then you would tell Handbrake to use those settings.

Ok, I think that we still are not quite understanding this.

If you want to encode to multiple formats you want to rip the DVD **without converting to another format to begin with.**

A DVD contains multiple VOB files that contain MPG-2 encoded data. So you want a ripper that will simply recreate the DVD files and structure onto your hard drive.

Handbrake can then **use that data from the hard drive.** That will be its source for whatever encoding that you want to do for the iPhone, etc.

---

### Post by PsychedelicWonders on 2009-04-20
> **Slim Odds said:**
> Ok, I think that we still are not quite understanding this.
 
If you want to encode to multiple formats you want to rip the DVD **without converting to another format to begin with.**
 
A DVD contains multiple VOB files that contain MPG-2 encoded data. So you want a ripper that will simply recreate the DVD files and structure onto your hard drive.
 
Handbrake can then **use that data from the hard drive.** That will be its source for whatever encoding that you want to do for the iPhone, etc.
 
But if I do it the way you are suggesting, this is going to give me the 4-8g files isnt it?
 
I do not want large files like that on my HDD.
 
Thats why I figured if I convert/transcode with the 1st rip, I will still have high quality digital rip for the computer/tv, yet still have a much smaller file.
 
Now I'm going to lose quality going to the iPhone anyways, so a transcode of the original rip/transcode will probably suffice. 
 
Technology just isnt there for the iPhone to be worth a high resolution transcode.

---

### Post by Slim Odds on 2009-04-20
> **PsychedelicWonders said:**
> But if I do it the way you are suggesting, this is going to give me the 4-8g files isnt it?
 
I do not want large files like that on my HDD.

That's your call. I, personally, don't consider that a lot a space to use temporarily.

> Thats why I figured if I convert/transcode with the 1st rip, I will still have high quality digital rip for the computer/tv, yet still have a much smaller file.
 
Now I'm going to lose quality going to the iPhone anyways, so a transcode of the original rip/transcode will probably suffice. 
 
Technology just isnt there for the iPhone to be worth a high resolution transcode.Once again, it's your call.
I just like to start with the best quality so that the output will also be the best possible.

---

### Post by PsychedelicWonders on 2009-04-20
> **Slim Odds said:**
> That's your call. I, personally, don't consider that a lot a space to use temporarily.
 
Once again, it's your call.
I just like to start with the best quality so that the output will also be the best possible.
 
But I thought the 1st rip/transcode is an EXACT digital copy...
 
If I transcode the actual DVD via the 1st rip or transcode it off of a full rip... I am still going to get the same quality transcode arent I?
 
I can see where I may lose some quality when transcoding it for the iPhone, but arent I  going to lose the same amount of quality when its converted to the iPhone format either way?

---

### Post by Slim Odds on 2009-04-20
> **PsychedelicWonders said:**
> But I thought the 1st rip/transcode is an EXACT digital copy...
 
If I transcode the actual DVD via the 1st rip or transcode it off of a full rip... I am still going to get the same quality transcode arent I?
 
I can see where I may lose some quality when transcoding it for the iPhone, but arent I  going to lose the same amount of quality when its converted to the iPhone format either way?

That is correct.

---

### Post by PsychedelicWonders on 2009-04-20
Ok, so I will rip/transcode once for the computer/tv & then transcode that file for the iPhone.
 
But what format do I want to rip if I only plan to keep it as a digital copy to play on computer/tv etc?
 
> an avi file with Xvid video encoding and mp3 audio that will be compatible with DivX-compatible DVD players, that's what you tell Handbrake to use when ripping the movie. If you want an mp4 file with h.264 video encoding and AAC audio, then you would tell Handbrake to use those settings. ?

---

### Post by PsychedelicWonders on 2009-04-20
In addition to my last post, what format is HB going to default to?
 
I would assume since I dont care about burning Divx DVDs, I would want this format:
 
> An mp4 file with h.264 video encoding and AAC audio, then you would tell Handbrake to use those settings.
 
Am I correct?
 
So will HB default to that transcode?

---

### Post by PsychedelicWonders on 2009-04-21
bump

---

### Post by mb_webguy on 2009-04-21
Handbrake defaults to its "Normal" preset, which is an mp4 with h.264 video, AAC audio, and no subtitles.

---

### Post by PsychedelicWonders on 2009-04-21
Ok, ripping now.

It just seemed to start "Scanning" right as I put the disc in since I had HB open.

But what do I do with that "Source" button?

Whats the easiest way/program to try and open this DVD to see if it ripped properly?

---

### Post by mb_webguy on 2009-04-21
The Source button lets you tell Handbrake what to encode.  I don't think I've ever put a DVD while Handbrake is open, so I have no clue if Handbrake will automatically detect it and choose it as the source.

---

### Post by PsychedelicWonders on 2009-04-21
I didnt do anything with the Source button, HB seemed to just start "scanning" on its own.

But I tried a DVD of my own and a DVD from netflix and this is what I came up with:

What am I doing wrong?

---

### Post by PsychedelicWonders on 2009-04-30
bump... still having issues I think.

---

### Post by mb_webguy on 2009-04-30
In the first screenshot, it doesn't look like you have any titles selected (in the top area).  Handbrake usually automatically selects the longest title on a DVD (which should be the movie), but if it doesn't, select it manually.

I the second, I'm a bit curious why you have the preview open.

In either case, what happens when you click Start?  And what happens when you manually select the source, instead of letting Handbrake do it for you (if that's actually what it's doing, which I've never encountered)?

---

### Post by PsychedelicWonders on 2009-05-11
When I have HB open and put a dvd in, it just begins to "scan titles" (see the progess bar at the bottom of HB in the attached picture)

Also, when selecting sources, I see I chose the DVD I want to burn, then it opens this screen and I dont know which file to choose to transcode?

---

### Post by PsychedelicWonders on 2009-05-12
bump...

---

### Post by PsychedelicWonders on 2009-05-13
bump

---

### Post by PsychedelicWonders on 2009-05-15
bump

---

### Post by PsychedelicWonders on 2009-05-17
bump

---

### Post by mb_webguy on 2009-05-17
When you're selecting a DVD as a source, you need to check that "Open VIDEO_TS folder" checkbox in the lower left of the Open dialog.  

As for the scanning thing, as I've said previously, I don't have Handbrake as my default application for opening DVDs, and haven't noticed that behavior on inserting a DVD.  I always have to select the DVD as the source manually.  Once I select it (by having the "Open VIDEO_TS folder" box checked and opening the VIDEO_TS folder on the DVD), Handbrake will scan the DVD, which just takes a few seconds, and automatically select the longest title (which is generally the movie).

---

### Post by PsychedelicWonders on 2009-05-25
Tried again and here is the progression:

It just seems to freeze on "scanning" now once I click the open button with everything checked & high lighted properly...

---

### Post by PsychedelicWonders on 2009-05-27
bump

---

### Post by calibre97 on 2009-05-30
I have Linux Mint (based on Ubuntu) on my Dell D630 and I have a Mac Mini with Mac the Ripper 2.66. Here's my workflow:
1. Insert DVD into Mac Mini.
2. Quit the DVD player that autostarts (gotta change that).
3. Run Mac the Ripper and save resulting directory.
   This gets me the VIDEO_TS folder and other stuff (maybe an AUDIO_TS folder as well, or other folders) others have talked about. With this, I now have the DVD in file form on a hard drive. I can use this as a basis for doing whatever I want. For example, I can put the DVD away and watch the movie on my Mac Mini with DVD Player. I can also now use HandBrake to convert that folder structure into whatever formats I want.
4. Copy the MOVIE_TITLE folder that contains the VIDEO_TS folder to my laptop. This is so I can use Toast Titanium to convert one movie, thus basically monopolizing the Mini, while I use HandBrake on the laptop to convert another one.
NOTE: As others have mentioned, each MOVIE_TITLE folder takes up anywhere from 4 to 8 GB of space.
5. On the laptop, run HandBrake and select the MOVIE_TITLE folder as the source. 
6. In HandBrake, select iPhone & iPod Touch under Apple in the Presets area to the right.
7. Click Start.

That's it. I get a resulting 961MB MOVIE_TITLE.mp4 file that I can now inport into iTunes and copy to my iPod.

Remember, I still have that MOVIE_TITLE folder so I can run HandBrake again and convert to another format if I wanted. Or, back on the Mac, I can burn another DVD of the movie with Toast, losing some fidelity in the process but basically getting another DVD that I can play just about anywhere I want.

Here's what it looks like:
(DVD) => MOVIE_TITLE folder on hard drive => MOVIE_TITLE.mp4 file.
So, there are now 3 versions of the movie:
1. Physical DVD
2. MOVIE_TITLE folder with VIDEO_TS (about 6GB in my case)
3. MOVIE_TITLE.mp4 file.

Again, now that I have the MOVIE_TITLE folder, I can safely put away the physical DVD and run HandBrake to make as many different conversions of the movie as I like. I only ever have the one copy of the MOVIE_TITLE folder. To save space once I'm done running conversions, I can always delete that folder to save space. If I ever need to do another conversion, I can always rip the physical DVD again (takes time of course), and work with the MOVIE_TITLE folder.

I hope this helps explain what's going on. I can't help with your HandBrake issues because it 'just worked' for me using the MOVIE_TITLE folder (again, actually ripped over on the Mac with Mac the Ripper, but it's irrelevant what tool you use so long as you wind up with that VIDEO_TS folder!) and the iPod Touch preset.

Good luck.

UPDATE: Interesting. Toast makes MV4 files which appear under TV Shows in iTunes and on the iPod, while HandBrake defaults to MP4 which appear under Movies in iTunes. Hmm. MV4 is available for "Container" in Handbrake, so I could easily choose that, but it doesn't matter. Both the MV4 and MP4 files play fine on the iPod.

---

