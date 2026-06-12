---
title: "CD burning with CD audio track names displaying on CD player?"
date: 2009-02-26
forum: General Help
---

### Post by Pipps on 2009-02-26
Hello

I would like to burn an audio CD from WAV files in Ubuntu.

I would like the CD to show the proper track names when it is played. 

In other words, I would like the text display on my CD player to show the individual audio CD track names as 'Song in F#', or Blues in C' - and not as 'Track1', 'Track2', which I understand is the default with most CD burning applications.

As anyone achieve this CD audio track-naming in Ubuntu?

Thanks

Pipps

---

### Post by Slim Odds on 2009-02-26
[http://en.wikipedia.org/wiki/CD-Text](http://en.wikipedia.org/wiki/CD-Text)

---

### Post by Pipps on 2009-02-26
Thanks for the link!

And [http://k3b.plainblack.com/about](http://k3b.plainblack.com/about)

Says that:
> CD-TEXT support. Will automagically be filled in from tags in audio files.

On this basis, I will give it a go and hope that it works!

:guitar:

---

### Post by Slim Odds on 2009-02-26
> **Pipps said:**
> On this basis, I will give it a go and hope that it works!


Do your WAV files have tags?

---

### Post by Pipps on 2009-02-28
Thank you for asking. And yes, I believe that the WAV files do have tags. When I exported the WAV files from Audacity, I believe it gave me the opportunity to save WAV tags for each individual WAV file. :)

I have attempted to check this again since. However, when trying to use kid3-qt to view the files' tags, it won't show me any information where WAV files are concerned. Darn it! :(

Would it be necessary for my WAV files to have tags in audio for the CD-text burning to work?

---

### Post by Slim Odds on 2009-02-28
> **Pipps said:**
> Would it be necessary for my WAV files to have tags in audio for the CD-text burning to work?

Where else to you think that the CD-Text will come from?

The CD-Text is put on the CD.

You can to it manually, when you burn the CD. But then you have to input all of the tracks by hand.

---

### Post by Pipps on 2009-03-01
> **Slim Odds said:**
> Where else to you think that the CD-Text will come from?
I assumed that the text would be taken from the individual WAV filenames? Is this a mistaken assumption?

And may I ask, how does a WAV tag differ from a WAV filename, and from an ID3V2 tag?

---

### Post by Slim Odds on 2009-03-01
> **Pipps said:**
> I assumed that the text would be taken from the individual WAV filenames? Is this a mistaken assumption?

And may I ask, how does a WAV tag differ from a WAV filename, and from an ID3V2 tag?

Tags are embedded within the file and contain much more information that just a filename.

Try google some time  :P
[http://www.id3.org/](http://www.id3.org/)

---

### Post by Pipps on 2009-03-01
Ah yes, you're right. Thank you for helping me get there with this! :)

---

### Post by Slim Odds on 2009-03-01
> **Pipps said:**
> Ah yes, you're right. Thank you for helping me get there with this! :)

You're welcome... glad to help...

---

### Post by Pipps on 2009-03-04
Hello!

I hope you can help me. I have run into a problem.

All of my WAV files have WAV tags - as Audacity saved them for me.

I am now attempting to use K3b to burn an Audio CD. When I add my WAV files to the K3b project, the column entitled 'filename' is populated fully, but the columns entitled 'Artist (CT-text)' and 'Title (CD-text)' are not populated at all.

How can I ask K3b to read the CD-text for both columns from the source WAV files themselves?

Thank you for your help.

Pipps

---

### Post by Pipps on 2009-03-19
I have not got any further on my own with burning CD-Text yet. 

I am hoping that someone out there has been able to successfully burn CD-Text with Ubuntu!

Please, somebody, tell me if you've been able to do it!

---

### Post by tm6148 on 2009-03-23
I've been struggling with this same problem myself.  My reading of the situation is that Audacity does not do Tags with WAV files, only MP3 files.  If you're exporting the tracks as WAV files, Audacity converts the _Labels_ you create into filenames, but there are no _Tags_ representing the Track, Artist, etc.  You can fill that information in relatively quickly in K3b before you burn the CD but here's the catch with that: not all playback software will recognize the encoded CD-Text information.  Here's what I've found with the ones I've burned with K3b: Windows Media Player with the WMPCDText plugin and RealPlayer will read it, iTunes 8 will not. In Ubuntu I haven't found anything that will read it except K3b itself.  Sound Juicer will not, despite what the Wiki says.

So as far as I can tell, it's a waste of time to try to burn the CD-Text information for playback in Ubuntu because no player that I've seen will display it.  I hope somebody will correct me there.

Ubuntu 8.04

---

### Post by tm6148 on 2009-03-23
> **tm6148 said:**
> 
So as far as I can tell, it's a waste of time to try to burn the CD-Text information for playback in Ubuntu because no player that I've seen will display it.  I hope somebody will correct me there.

Ubuntu 8.04

Based on what I saw in another thread, I tried Audacious with the extra plugins, but that didn't seem to work either.

---

### Post by Pipps on 2009-03-24
Hi TM

You are right - I have also learnt that Audacity strangely does not export WAV tags. Oh, why can't it be more like the CollEdit of old which it so earnestly appears to be trying to emulate!

My reason for wanting to burn CD-text with a WAV CD project is that I have a home hifi CD player which can read CD-text. It does so with certain special retail CDs, you see!

I wish there was linux software which was up to this simple task!

---

### Post by Slim Odds on 2009-03-24
> **Pipps said:**
> I wish there was linux software which was up to this simple task!

It's not a linux problem. The WAV file format has no provisions for embedding that information.

As was mentioned, many CD burning programs allow you to enter that information.

---

