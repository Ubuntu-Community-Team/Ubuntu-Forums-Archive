---
title: "Stardict TTS"
date: 2009-05-17
forum: General Help
---

### Post by charrah on 2009-05-17
I want Stardict to run an alternate TTS (a script really) but even when I type anything in the "Use TTS program" box, nothing changes. Either the default TTS reads it if I specify that it should pronounce the word, or nothing does. The script does work, it is not being run. So exactly what options do I need to get Stardict to run other TTS?

---

### Post by jukzh on 2010-04-30
> **charrah said:**
> I want Stardict to run an alternate TTS (a script really) but even when I type anything in the "Use TTS program" box, nothing changes. Either the default TTS reads it if I specify that it should pronounce the word, or nothing does. The script does work, it is not being run. So exactly what options do I need to get Stardict to run other TTS?
Well a bit late, but anyway
```
rm /usr/lib/stardict/plugins/stardict_espeak.so /usr/lib/stardict/plugins/stardict_festival.so
```
And try again!
By the way this sounds nicer than espeak festival stuff
```

#!/bin/bash
ARG="$1";
if [[ ${#ARG} -gt 0 ]]
then
  mplayer http://translate.google.com/translate_tts?q="$ARG"
else
while read INPUT
 do
  mplayer http://translate.google.com/translate_tts?q="$INPUT"
 done
fi

```
I call it gsay.sh %s or 
```
echo %s | gsay.sh
```
Cheers!

---

### Post by charrah on 2010-05-02
A bit late, but thanks anyway. I would use Google only the trouble is that I was intending to use the TTS on Japanese and Google's doesn't support it; there was a particularly good one for SAPI I ran under Wine, at least. Your script works for me using English though.

---

### Post by jukzh on 2010-05-05
> **charrah said:**
> A bit late, but thanks anyway. I would use Google only the trouble is that I was intending to use the TTS on Japanese and Google's doesn't support it; there was a particularly good one for SAPI I ran under Wine, at least. Your script works for me using English though.
I'm glad that you're still here, you getting email notification? how to turn it on for me, if you are. You turned me on with tts, cause i'm Chinese leaner, i found [here]("http://www.mdbg.net/chindict/chindict.php?page=cedict") file called CEdict, there's gotta be something similar, JEdict too for your case, i don't know.
So here's demo, well it's not exactly mandarin but similar.
And don't give up! (imho)
```
#!/bin/bash
CEDIC="$HOME/tmp/cedict_ts.u8"
ARG="$1"
if [[ ${#ARG} -gt 0 ]]
then
echo $(cat $CEDIC | grep "$ARG" | sed -n '1p' | tr ' ' '_' | awk '{split($1,A,"[")split(A[2],B,"]");print B[1] }' | tr -d '[0-9]' | tr '_' ' ') | festival --tts 
else
while read INPUT
do
echo $(cat $CEDIC | grep "$INPUT" | sed -n '1p' | tr ' ' '_' | awk '{split($1,A,"[")split(A[2],B,"]");print B[1] }' | tr -d '[0-9]' | tr '_' ' ') | festival --tts
done
fi
```
Regards,
jk

---

### Post by charrah on 2010-05-05
Yeah I get emailed on new posts. If you want notification for a particular thread, click, Thread Tools -> Subscribe to this Thread just above the first post. I think there is an option somewhere in the User CP for auto-subscribing but haven't looked.

Yeah there is JEdict and a couple other good dictionary projects out there, although it's not directly linked with a TTS usually cause in Japanese all kanji that have a couple readings depending on their context (most just have 2 easily distinguishable ones though), and the intonation is more about the type of sentence than the raw meaning of the word, so dictionary isn't everything.

I figure I'm gonna try out OpenSAPI sometime (project to make SAPI work really well with Wine and integrate well with Linux apps), cause I have a really dependable TTS, it just doesn't work very conveniently in Wine.

Good luck (and most importantly have fun) learning Chinese!

---

### Post by jukzh on 2010-05-06
Thanks, you too!

---

