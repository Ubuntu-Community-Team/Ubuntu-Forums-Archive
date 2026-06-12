---
title: ".avi files - What dependencies."
date: 2005-11-19
forum: Desktop Environments
---

### Post by UbunuAndrew on 2005-11-19
Hello,

I am trying to watch .avi files in my Totem Player but am having absolutely NO luck in doing so. Any help on what I need to download and install would be very greatly appreciated.

Thanks in advance,
Andrew West

---

### Post by GeneralZod on 2005-11-19
Hi Andrew,

Have you tried installing w32codecs? If not, do a search for this term on the forums - it comes up pretty often :)

Cheers,
Simon

---

### Post by UbunuAndrew on 2005-11-19
I have tried installing them. I also download wmplayer and installed it. They both are whining to me about a missing stream. I am going to try and download another .avi file that is much smaller in size just to see if it is my movie that I am trying to view opposed to the system itself.

---

### Post by taurus on 2005-11-19
Personally, I would go for mplayer.  You can install it using synaptic after adding those to your /etc/apt/sources.list

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse

And for codecs, you can download one from [http://www.mplayerhq.hu](http://www.mplayerhq.hu) or do a search in synaptic...

p.s.  Okay, download this codecs, [http://www2.mplayerhq.hu/MPlayer/releases/codecs/all-20050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/releases/codecs/all-20050412.tar.bz2), and save it somewhere.  Then, do

tar xvjf all-20050412.tar.bz2
sudo mkdir /usr/lib/win32
cd all-20050412
sudo cp -R * /usr/lib/win32

---

### Post by UbunuAndrew on 2005-11-19
An update: It is 'not' just the .avi file. I am having trouble pulling video from mpeg (mpg as well) files, and am just getting sound. Unfortunately I am getting 'nothing' for .avi's period though.

---

### Post by UbunuAndrew on 2005-11-19
After a few minutes of my system wanting to whip my butt and it screaming at me. 

"Broadcast Message: You're killing me. Use VLC player."
"Hey it's not going to work. Use VLC player"
"I highly doubt that's what you wanted to do - use VLC player"

I decided to try VLC player.. and it worked. Thank god for my systems AI. :-D

---

### Post by unixfudotnet on 2005-11-21
n00b

---

### Post by Hairy_Palms on 2005-11-21
hmmm first troll ive seen on ubuntu forum since i joined.

---

### Post by unixfudotnet on 2005-11-22
not a troll.

andrew has no clue about anything, and just repeats what others have told him as if he knew.

i would take caution regarding any advice he gives, as he doesn't know what he is talking about.

he is also a person who has stolen open sourced code and changed the copyright to be his and then pass off the code as his. 

not only is he clueless and trying to pass off as if he does know what he is talking about, he is also unethical as he doesn't have respect for opensource.

i unfortunately/fortunately know him in real life. he tends to do the same thing on pretty much every forums he goes to.

please be aware and causious. 

he thinks machines talk to him and he rm -rf /'d his own machine after someone told him to, and gives people accounts to his machines that he doesn't trust.

it is fine to be a newbie, we all were, but there is a difference between just being a newbie who asks for help and has a desire to learn and doesn't steal open source code as their own, and those that try to be more than they are and words and code they repeat have been just other things people have told them. andrew is the later.

he posted things people have said about issues on this forums (verbatim) to the staff email list at his work, trying to play it off like he said it and understood things.

this is not a troll post, as it is all facts and first hand account of his actions.

he is known as a "n00b", dishonest, and not willing to ask for help and listen to other's help at the expense of coworkers and the company he works for.

---

### Post by Stinky_Pinky on 2005-11-22
I will second everything unixfudotnet has said and we all have proof as well.  I'll leave it at that.  Whoever thinks that ubuntuandrew was being attacked should read his AI post once again.  Since when does Ubuntu have AI that tells you with a system broadcast message what Video player to use?

---

