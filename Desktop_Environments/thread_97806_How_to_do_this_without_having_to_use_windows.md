---
title: "How to do this without having to use windows?"
date: 2005-12-01
forum: Desktop Environments
---

### Post by fannymites on 2005-12-01
I've just got bluetooth running on ubuntu and am having fun sending files to my Sony Ericcson k700i but there are a couple of issues I'm having.

Firstly, are there any apps available for ubuntu that will allow me to convert video files into a format compatible with k700i since it won't play anything I've sent from my pc, only ones I've sent from other phones.

Secondly, there is an issue when using the vodafone branded k700i (and others) 
that means mp3 files can't be used as ringtones unless they have some sort of digital rights management (DRM) tag.
I have an app for windows that allows me to add this tag to mp3 files but I can't find any way to do this in linux.  Anyone know a way of doing it?
I believe the DRM issue can also be bypassed by converting the mp3 file into a certain format, does anyone know what the format is and how I can do it in linux?

---

### Post by Jussi Kukkonen on 2005-12-02
Google is usually pretty good with stuff like this.

Searching for sony *ericsson k700i linux * gives results that seem to answer your question about DRM ([1]("http://www.lysator.liu.se/~torkel/computer/k700/files.html"), [2]("http://www.hentges.net/misc/k700i/index.shtml")).

...Forgot the other question: If the phone plays H.263 video, ffmpeg will probably do the job with the correct codec. Maybe someone else can tell where to get it (I didn't check the repositories, this could be as easy as *apt-get install ABC*)...

---

### Post by fannymites on 2005-12-02
Thanks for the links, I had spent many many hours googling and had found quite a lot of information but much of it didn't work or the apps suggested weren't available for linux.  Or maybe I'm just crap at finding the right keywords.
I have already seen the second link and tried the command at the bottom but I still couldn't use the files as ringtones.
I had also seen mention of NCPT along with many other softwares (I have a couple in Windows) but I wasn't aware NCPT worked on linux.
The command in the first link seems to be working ok and I will use that from now on.

Regarding videos I read a forum thread which showed how to do it with a script and with ffmpeg compiled with AMR support but I couldn't get this working either.
I've also found an app for linux which is supposed to convert any media file into 3GP format but I'm yet to find a single video file it will import.

---

### Post by fannymites on 2005-12-02
Sorry, I misunderstood what the command was doing, it was just downsampling the file not changing the DRM content.
As for the Nokia Mobile Internet Toolkit, I cannot find any version anywhere for linux.
I'll just keep using windows to add drm content and convert video files, it's much less hassle.

---

