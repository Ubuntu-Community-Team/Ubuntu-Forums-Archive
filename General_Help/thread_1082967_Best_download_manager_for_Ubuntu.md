---
title: "Best download manager for Ubuntu?"
date: 2009-02-28
forum: General Help
---

### Post by S3loth on 2009-02-28
What I am doing is downloading all the episodes of Rev3's Pixel Perfect from a .txt file I got on the [forums]("http://revision3.com/forum/showthread.php?t=24179&highlight=download"). It has the URLs to all the episodes so I can download them. I have had some problems with downloads in the past, (with programs like as down Them all!) such as when I pause and then go to unpause them they will start over again. What I need is a program that will let me start all these downloads, pause, turn off my computer or whatever and still take off from where the download was paused.

---

### Post by InspiredIndividual on 2009-03-01
Maybe it's easiest to use wget from the command line? I'm not sure it's the best downloader, as my experience with command line tools is rather limited. For example, to retrieve the files indicated in your textfile:

```
wget --input-file=file --no-clobber --background --continue
```

Be aware that I haven't tried the code myself, but it should work. 'file' should be your txt-file, the no-clobber option ensures files won't be downloaded twice. The background option puts the download process in the background immediately. The continue option is useful for files that have been retrieved only partially when you shutdown your computer, but it's not supported by all servers. If the individual files are small, you may want to run the command without this option to ensure you will have downloaded all files correctly when all downloads are finished.  After a shutdown and startup, just issue the same command again to resume your download. See the wget man pages for more information. 

Useful options in your particular situation might be --limit-rate=amount to limit download speed, --directory-prefix=prefix to set the directory you want to save the downloaded files. If the websites you're downloading from try to prevent automated retrieval programs such as wget from working by applying statistical analysis, you might have use for the --random-wait option as well.

---

### Post by avrilrox on 2009-03-01
I don't think you could pause your downloads using Wget.

I'd suggest installing Wine and running Orbit Downloader Manager. I think it's the best download manager.

---

### Post by binbash on 2009-03-01
you can use wget or downthemall extension for firefox

---

### Post by Vaphell on 2009-03-01
someone made torrent

[http://thepiratebay.org/torrent/4501899/PixelPerfect_Pixel_Perfect_with_Bert_Monroy](http://thepiratebay.org/torrent/4501899/PixelPerfect_Pixel_Perfect_with_Bert_Monroy)

---

### Post by InspiredIndividual on 2009-03-01
> **avrilrox said:**
> I don't think you could pause your downloads using Wget.


Why not? I think you can just terminate the wget process to pause, and issue the same command again to resume. What's the reason this should fail?

---

### Post by jmszr on 2009-03-02
S3loth,
        I just ran a search in Miro (available in Synaptic or Add/Remove) and Pixel Perfect is available there and I know you can start/stop/resume multiple downloads with Miro (at least if it's available in Miro).

---

