---
title: "Speech recognition"
date: 2008-12-07
forum: General Help
---

### Post by afbainbridge on 2008-12-07
For years I've used Dragon 'Naturally Speaking' running under Windows to save time when creating documents - it speeds up my word processing and gets around my poor keyboard skills.  It can be used in e-mails too.  Does anyone know of an equivalent open-source speech recognition application which would run in Ubuntu?

---

### Post by geear on 2008-12-07
I've been hunting for the same thing for awhile, not much success yet. It seems like there were a bunch of projects started several years ago but most of them seem dead now.

What version of Dragon do you have? I know some versions work fairly well if you use WINE ([http://www.winehq.com](http://www.winehq.com)), but you have to dictate into Dragon's "text pad" area and then copy it over to OpenOffice.

Maybe someone else can give some other suggestions...

G.

---

### Post by spiderbatdad on 2008-12-07
there is Festival:[http://www.xenocafe.com/tutorials/php/festival_text_to_speech/index.php](http://www.xenocafe.com/tutorials/php/festival_text_to_speech/index.php)
It is in synaptic package manager. Try opening the package manager and typing speech recognition into the quick search box.

Also see:
[http://linux.softpedia.com/get/Documentation/Speech-Recognition-HOWTO-18398.shtml](http://linux.softpedia.com/get/Documentation/Speech-Recognition-HOWTO-18398.shtml)

---

### Post by KittyChunk on 2009-06-09
Note that Festival is speech *synthesis*, not speech *recognition*. It does text-to-speech and not speech-to-text like Dragon and its ilk.

I've also been interested in the speech recognition problem from time to time, for the same reasons as the original poster. It could also improve accessibility in Ubuntu for people with disabilities, but it's a huge and complex task to do it successfully. 

The Julius and CMU-Sphinx projects look to be coming along well. Julius was originally designed for Japanese though and I'm not sure how far along the acoustic models for English are - VoxForge was working on them the last time I checked.

---

### Post by rvk on 2009-08-21
VoxForge still needs many hours of speech before acoustic models that make dictation possible will become available.The current English acoustic model is based on about 70 hours of speech. For command and control that is decent, but for dictation much more would be required. Though someone who submits three hours of speech might get usable results. A nice way to contribute would be to record some chapters of a book at [LibriVox.org]("http://librivox.org")and then submit the speech and the text in an uncompressed file format (i.e. no MP3 for example) to VoxForge.

A much simpler method would be to go to VoxForge.org and to use the online speech submission app. However, that's a lot more tedious.

---

### Post by john1066 on 2010-11-05
Any progress on this in the last two years. I'm also looking for something equivalent to Dragon Nat speak.

John

---

### Post by Meuro on 2010-11-12
*bump* *bump*

Its been just over a year now since the last post.

Has there been any developements in speech-to-text since then?  This type of tool is something that would be very useful to me particularly if it can take speech from audio files


Thanks,
Meuro

---

### Post by Soul-Sing on 2010-11-12
There is no such thing as the great DNS software for linux, but there are several projects which are related to a very old IMB project ViaVoice, such as voxforge. But they are really not as good as DNS.
There are attempts to get it up and running via Wine. It didn't work on my computer...I whish I could use it.(on linux)

---

### Post by nrundy on 2010-12-18
I too would like speech to text capability in Ubuntu.  Windows 7 now has speech to text natively. One of the few things about Windows that leaves ubuntu wanting :(

---

### Post by Younio on 2011-03-08
I wonder...
             I know there is some Google app in android OS that recognizes voice, by connecting to Google server, and android is Linux and open source and the app is Google's (open source?) So in theory it should be possible to make it work on any Linux distribution.

---

### Post by honeybear on 2011-06-12
> **KittyChunk said:**
> Note that Festival is speech *synthesis*, not speech *recognition*. It does text-to-speech and not speech-to-text like Dragon and its ilk.

I've also been interested in the speech recognition problem from time to time, for the same reasons as the original poster. It could also improve accessibility in Ubuntu for people with disabilities, but it's a huge and complex task to do it successfully. 

The Julius and CMU-Sphinx projects look to be coming along well. Julius was originally designed for Japanese though and I'm not sure how far along the acoustic models for English are - VoxForge was working on them the last time I checked.

**Can SPHINX2 work with USB microphone?**

[http://box-look.org/content/preview.php?preview=1&id=142465&file1=142465-1.jpg&file2=142465-2.jpg&file3=&name=NightlyStar](http://box-look.org/content/preview.php?preview=1&id=142465&file1=142465-1.jpg&file2=142465-2.jpg&file3=&name=NightlyStar)


-- 
reco voice: [http://freespeech.sourceforge.net/](http://freespeech.sourceforge.net/)

---

### Post by JackomoLight on 2013-02-02
> **Younio said:**
> I wonder...
             I know there is some Google app in android OS that recognizes voice, by connecting to Google server, and android is Linux and open source and the app is Google's (open source?) So in theory it should be possible to make it work on any Linux distribution.

I am sure it could be made to work on linux though it will be against google s licenses and what not. However I am willing to work on it if anybody else is interested? After all Google Voice search app is supremely accurate .... I wish they had an API

---

### Post by honeybear on 2013-02-03
> **JackomoLight said:**
> I am sure it could be made to work on linux though it will be against google s licenses and what not. However I am willing to work on it if anybody else is interested? After all Google Voice search app is supremely accurate .... I wish they had an API

```
ls -ltrah "$TARGETFLAC"
if  [ ! -f "$TARGETFLAC" ] ; then 
  echo "error"
  exit
fi
echo "** Step 2 **  Submit to Google Voice Recognition"
wget -q -U "Mozilla/5.0" --post-file "$TARGETFLAC" --header="Content-Type: audio/x-flac; rate=16000" -O - "http://www.google.com/speech-api/v1/recognize?lang=en-us&client=chromium" >      "$TARGETRET"
cat "$TARGETRET" 
TXTMSG=` cat "$TARGETRET" | awk -F '","confidenc'  ' {  print $1 } ' | awk -F '"utterance":"'   ' { print $2  } '` 
```

---

### Post by Bucky Ball on 2013-02-03
***Thread closed***

Necromancy. Thread has been dead and inactive for over a year. Please post a new thread with issues/questions/problems.

---

