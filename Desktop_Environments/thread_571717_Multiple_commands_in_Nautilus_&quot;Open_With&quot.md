---
title: "Multiple commands in Nautilus &quot;Open With&quot;?"
date: 2007-10-09
forum: Desktop Environments
---

### Post by zach014 on 2007-10-09
I'm trying to make it so that when I open any MP3, it will convert it to an OGG (using "soundconverter -b") *and* play it in totem simultaneously. Also it'd be helpful if I could have it check whether the OGG already exists before executing the soundconverter command.

Thanks,
zach

---

### Post by kelbizzle on 2007-10-09
There may be a gnome script here that may be able to help you. 

[http://g-scripts.sourceforge.net/index.php](http://g-scripts.sourceforge.net/index.php) '

I would check there first.

---

### Post by zach014 on 2007-10-09
well i'm really looking for something like a variable i could use to specify the file, like firefox has the %u for the url. i could do the rest pretty easily

---

### Post by Lord Illidan on 2007-10-09
Try this script :

```
#/bin/sh
soundconverter -b $1 & totem $1
```

I'll check if I can get it to check for an mp3 of the same name.

---

### Post by zach014 on 2007-10-10
well actually, check for an ogg of the same name
so, with the script, wouldn't $1 have to be defined first?
also, when i try making it open with that script, it says "Could not find application" "Could not find '/home/zach/Desktop/mp3-script'"
and when i just entered the command "soundconverter -b $1 & totem $1" for open with, it just did nothing (leading me to defining the variable)
~zach

---

### Post by Lord Illidan on 2007-10-10
My apologies for not explaining.
When used in a script, $1 is the name of the first *argument* given to to the script.

Thus, it is "defined" at runtime, so to speak.

To run it, you must first make it executable. Let's say you save it as mp3script.sh. To make it executable, just ```
chmod +x mp3script.sh
``` in that directory.

To run it, pass an mp3 as an argument.

Thus, given an mp3 test.mp3, I would call it like this :
```

./mp3script.sh test.mp3
```

Then you can even set it as a nautilus Open With action.

---

### Post by zach014 on 2007-10-10
ah yes, i often forget to chmod my files

---

### Post by zach014 on 2007-10-10
alright now i have a slight problem
say i have an mp3 like "Artist - Track Name.mp3"
when i use this script, it only opens up Artist (since the rest is cut off by the spaces)
im not sure if this is nautilus' fault or the script's and nautilus'. im guessing it's just the script's, so how would i go about fixing this? like adding in quotes to the argument to sounconverter -b or totem
im sure this'd fix it, but i'm not sure how to do it

---

