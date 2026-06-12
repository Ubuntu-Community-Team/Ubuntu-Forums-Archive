---
title: "how can i edit?"
date: 2005-07-18
forum: Desktop Environments
---

### Post by masfenix on 2005-07-18
Hi,
I have kino video editor, but everytime i try opening a avi file, it says "failed to load media".

How can i fix that?

---

### Post by damonw5 on 2005-07-18
[QUOTE=masfenix]Hi,
I have kino video editor, but everytime i try opening a avi file, it says "failed to load media".

How can i fix that?[/QUOTE]
Listen to what "Schirmacher" had to say in 2002 on [http://kino.schirmacher.de/dcforum/dcforum?az=show_topic&forum=105&topic_id=6&mesg_id=6&page=](http://kino.schirmacher.de/dcforum/dcforum?az=show_topic&forum=105&topic_id=6&mesg_id=6&page=)

"AVI files contain compressed video, and to display the contents the software must decompress the video data. There are many different compression schemes implemented, so many different software decoders are required.

Kino has only one codec for handling the DV compression scheme. Therefore it can only display AVI files containing this particular type of video data.

Earlier versions of Windows, on the other hand, come with a lot of codecs, but the DV codec is missing. Therefore these Windows systems can display most AVI files, with the exception of Kino's and dvgrab's AVI files.

The easiest way of installing the missing codec on a Windows system is to install a demo version of an arbitrary video editing software, which will also install the missing codec. The codec will usually work even after the demo version has expired." (end quote)



I don't know much about kino, but this may be worth a try:

* Enable extra repositories: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
* Using Synaptic (Under System->Administration), search for and install the package called "w32codecs". You may also want some of the other codecs listed here: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

---

### Post by masfenix on 2005-07-18
[QUOTE=damonw5]Listen to what "Schirmacher" had to say in 2002 on [http://kino.schirmacher.de/dcforum/dcforum?az=show_topic&forum=105&topic_id=6&mesg_id=6&page=](http://kino.schirmacher.de/dcforum/dcforum?az=show_topic&forum=105&topic_id=6&mesg_id=6&page=)

"AVI files contain compressed video, and to display the contents the software must decompress the video data. There are many different compression schemes implemented, so many different software decoders are required.

Kino has only one codec for handling the DV compression scheme. Therefore it can only display AVI files containing this particular type of video data.

Earlier versions of Windows, on the other hand, come with a lot of codecs, but the DV codec is missing. Therefore these Windows systems can display most AVI files, with the exception of Kino's and dvgrab's AVI files.

The easiest way of installing the missing codec on a Windows system is to install a demo version of an arbitrary video editing software, which will also install the missing codec. The codec will usually work even after the demo version has expired." (end quote)



I don't know much about kino, but this may be worth a try:

* Enable extra repositories: [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
* Using Synaptic (Under System->Administration), search for and install the package called "w32codecs". You may also want some of the other codecs listed here: [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)[/QUOTE]
 Already done that. 
What else?

---

### Post by abmcr on 2005-07-28
I have installed the w32codecs but the problem continue. :-| 
What it is necessary to do? Thank you

---

