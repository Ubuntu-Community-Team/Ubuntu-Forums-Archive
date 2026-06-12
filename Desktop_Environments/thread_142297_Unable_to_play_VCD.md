---
title: "Unable to play VCD"
date: 2006-03-10
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-03-10
I got a VCD, which played just fine on a WIN machine.
Under Ubuntu, the .dat files are recognized as **plain text documents**, and when I try to open them through xine the application will say it hasn't got the right codecs.
Text Manager or Leafpad, don't manage to open the files neither (surprise, surprise...)

G

---

### Post by MichaelZ on 2006-03-10
Hello,

Did you install the Multimedia Codecs? Have a look at here:

[http://ubuntuguide.org/#xine-ui](http://ubuntuguide.org/#xine-ui)

Eventually, you can try with another player and see if it can play it.

Best wishes,
Michael

---

### Post by GabrielWolff on 2006-03-10
[QUOTE=MichaelZ]Hello,

Did you install the Multimedia Codecs? Have a look at here:

[http://ubuntuguide.org/#xine-ui](http://ubuntuguide.org/#xine-ui)

Eventually, you can try with another player and see if it can play it.

Best wishes,
Michael[/QUOTE]

Gone through the guide, followed it
 xine still doesn't read it, but here's smething weird:
totem does, but: 
1) I can't navigate between the tracks. It's playing them in a row, but the ff and bwd buttons aren't highlighted
2) One of the five tracks is missing.

And still nautilus says it's plain text files

G

---

### Post by MichaelZ on 2006-03-10
[QUOTE=GabrielWolff]xine still doesn't read it, but here's smething weird:
totem does, but: 
1) I can't navigate between the tracks. It's playing them in a row, but the ff and bwd buttons aren't highlighted
2) One of the five tracks is missing.
[/QUOTE]

May be your file is corrupted. May be when you tried to open the file with a text editor you corrupted it.

[QUOTE=GabrielWolff]And still nautilus says it's plain text files[/QUOTE]

I think that nautilus says so, because the .dat are associated to text type (mime type). You should check how the .dat are associated (or which application is selected to be used to open these files).

Best wishes,
Michael

---

### Post by GabrielWolff on 2006-03-10
[QUOTE=MichaelZ]May be your file is corrupted. May be when you tried to open the file with a text editor you corrupted it.

Best wishes,
Michael[/QUOTE]

Thought so, but the .dat file is on a CD, so it can't really get corrupted (other than by a Feuerzeug or a Fingernagel, ah?).
And that still doesn't explain the fact that I'm unable to navigate through the files. That shouldn't be the case, should it?

?

G

---

### Post by MichaelZ on 2006-03-10
[QUOTE=GabrielWolff]Thought so, but the .dat file is on a CD, so it can't really get corrupted (other than by a Feuerzeug or a Fingernagel, ah?).
[/QUOTE]

Yes, I think so :).

[QUOTE=GabrielWolff]
And that still doesn't explain the fact that I'm unable to navigate through the files. That shouldn't be the case, should it?
[/QUOTE]

Navigate through the by using File Browser or similar you mean?

AFAIK ubuntu has some player packages, which you can give a try until you find a good one. Personally, I would give a try to VLC media player ([http://www.videolan.org/vlc/](http://www.videolan.org/vlc/)) :). ubuntu has this, but I do not remember if in the universe or multiverse repository. Just use Add Applications. 

Best wishes,
Michael

---

### Post by GabrielWolff on 2006-03-10
Worked, solved, great, thank you
Was in the universal
Went smooth like a piece of Sachertorte ;-)

G

---

### Post by MichaelZ on 2006-03-10
[QUOTE=GabrielWolff]Worked, solved, great, thank you
Went smooth like a piece of Sachertorte ;-)
[/QUOTE]

I am happy that it works.

Sachertorte.....I like it :D.

Best wishes,
Michael

---

### Post by vpjr on 2007-05-03
MichaelZ,

I want to add my thanks.  Read your advice just an hour ago and now I'm watching my VCD.

---

