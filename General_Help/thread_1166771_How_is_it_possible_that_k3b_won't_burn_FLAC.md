---
title: "How is it possible that k3b won't burn FLAC?"
date: 2009-05-22
forum: General Help
---

### Post by ricardisimo on 2009-05-22
I've installed all codecs as per one or two other similar threads, but still get:

```
Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.
```
Thanks in advance for any help.

---

### Post by ricardisimo on 2009-05-26
Brasero seems to work, but it is such an ugly, slow program that I'd prefer working the bugs out of K3B if possible. Any ideas? Thanks.

---

### Post by ricardisimo on 2009-05-28
I would mark this as solved, if I could. I installed flac via synaptic (all of the "libflac" variants were already installed.) It didn't work, then I reposted here. Since that time my computer has been restarted, which I didn't think was necessary in linux, but it's the only thing that I can think of to explain the fact that now I can burn flac files with K3B. My thanks to everyone for helping to turn me into my own personal thread killer.

---

### Post by ricardisimo on 2009-07-12
I think I've figured out the problem (or at least one problem among others). Flac files encoded in 24-bit bit depth, as opposed to 16-bit, are problematic for both k3b and brasero.

---

### Post by falkTX on 2009-07-23
why not:
```
ffmpeg -i name.flac output.wav
```

That will convert the flac to wav, making it "burnable"

---

### Post by ricardisimo on 2009-07-26
Yeah, but not only does flac save some space, but my point is that I shouldn't have to do anything to a flac file that I wouldn't have to do to an mp3, ogg or wav. It should be a fully supported format. The title says it all: "How is it possible...?" It shouldn't be a problem, but it is.

Evidently k3b and brasero do not recognize flac files encoded in 24-bit depth. The solution is simple: change the default setting in Audacity back to 16-bit, and stop producing the problematic flac files. I'm hoping that is the end of it.

Is this a bug in either Audacity on the one hand, or in k3b and brasero on the other? Should I report this?

---

### Post by darolu on 2009-07-26
I don't use KDE, but I suppose Amarok can burn audio CD's; I know Rhythmbox can.

---

### Post by ricardisimo on 2011-12-05
I'm not sure why I marked this as solved. Shouldn't 24-bit flac be an option for people?

---

