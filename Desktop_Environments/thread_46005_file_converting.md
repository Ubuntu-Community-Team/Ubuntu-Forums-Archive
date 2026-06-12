---
title: "file converting"
date: 2005-07-02
forum: Desktop Environments
---

### Post by Terracotta on 2005-07-02
Hye,
Is there an easy way (program) to convert wma and mp3 to ogg vorbis?? and wav, wmv .... to xvid or something open source???
I'd just like to convert my files to an open source variant. But I haven't found a linux program that does this. Oh and one more question, is there a big quality loss of you convert from one algorithm to another?
Tx.

---

### Post by Stemp on 2005-07-02
Wma to ogg
```
#!/bin/bash
#
# Dump wma to wav (first step in conversion)

for i in *.wma
do
mplayer -ao pcm "$i" -aofile "$i.wav"
done

#Second step... convert

for i in *.wav
do
oggenc -b 160 "$i"
done

# Remove extrenuous extensions

for i in *.ogg
do
x=`echo "$i"|sed -e 's/wma.ogg/ogg/'`
mv "$i" "$x"
done

# Remove files

rm -f *.wma* 
```

---

### Post by Terracotta on 2005-07-02
euh??? I'm really glad you're trying to help, but I don't understand a thing of it, do I have to write the for .... also in the terminal?? Maybe I should have told you I'm just a noob kind of guy :$, but willing to learn though. :-). I also don't have mplayer I suppose I don't have the right repositories activated since I can't install them, but when I add more repositories I get a lot of errors. (universe, multiverse ... are enabled, kde 3.4.1 and koffice 1.4 are enabled as well).
Tx for the quick response though.

---

### Post by Stemp on 2005-07-02
Sorry,

I've seen «Terracotta 5 Cups of Ubuntu» ;)

So with gedit create wma2ogg.sh
Copy the lines (you may forget the rm part)

And the in a terminal : ./wma2ogg /home/user/*.wma

---

### Post by Terracotta on 2005-07-02
ha, lol, well I guess the five cups is because I somehow can post replies to some peoples problems, but I'm really quite a newbie :-), sorry for confusing you.

Edit:
where were my manners: thank you :)

---

