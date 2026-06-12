---
title: "No sound in OpenOffice Impress (dapper specific?)"
date: 2006-03-25
forum: Desktop Environments
---

### Post by eqisow on 2006-03-25
I am currently been unable to get sound to work in OpenOffice Impress. I am running Dapper and the latest version of OOo from the repositories. I rarely use Impress, so I cannot be sure whether this is specific to Dapper or not. 

There is no option for sound under the Insert --> Object menu. Also, adding sound to slide transitions does not work. I have tried with multiple files and formats to no avail. I have w32 codecs installed and have no trouble with any other media files.

I know this is probably a very rarely used feature, but the college professor says it *has* to have sound (wtf?), so any help would be greatly appreciated.

---

### Post by rsay on 2006-03-25
Sound doesn't work out of the box on breezy, it may be the same way on Dapper. 

For breezy I have the ooffice 2.01 installed by automatix. On top of that I had to install the Java Media Framework from Sun and change some things in the openoffice java preferences. Last but not least, the menu option never shows up but you can add the movie/sound button to your toolbar via the toolbar customization. 

I used the second post in this thread from the ooffice forums to get mine going:[http://www.oooforum.org/forum/viewtopic.phtml?t=26704&highlight=jmf+jmfhome+sun]("http://www.oooforum.org/forum/viewtopic.phtml?t=26704&highlight=jmf+jmfhome+sun")](*,)

I'm doing a talk with a "rock and roll flashback" subtheme which motivated me to get this figured out. I'm not sure why the JMF isn't a requirement for openoffice in Breezy. I had hoped that this problem would solve itself in Dapper. Openoffice is a cornerstone piece of productivity software and should just work.

---

### Post by eqisow on 2006-03-25
I followed your instructions and now have sound in OOo. I still can't get a sound entry on the Insert --> Object menu, but this isn't really a huge deal. So yeah, many thanks for your help!

One final question, I have read that sound from PowerPoint will not import correctly to Impress. If I save an Impress file with sound as a PowerPoint file, will it import to powerpoint correctly?

---

### Post by baddemanax on 2006-05-31
:Hi all,


I have the same problem. I did the procedure explained above, then I could hear some sound. ( i use the latest dapper( kubuntu), and do the upgrade on daily basis)

But when I added the missing button in the insert -> object-> sound or -> movie. They are not enabled.

I also tried with the java jmstudio and when I play an AVI, mpeg ... i get the sound but no picture ( black screen)?

I am currently back to windows power point, because till now this is the only way for me to get the video and sound in a presentation  ..... :( 

if someone of you has an idea....

should this not be put in a bug report ?

---

### Post by TravMan63 on 2007-06-06
Can you upgrade Impress to 2.2?
Sound (mp3, ogg) is running fine on 7.04 Fiesty (but having problems with video)

---

