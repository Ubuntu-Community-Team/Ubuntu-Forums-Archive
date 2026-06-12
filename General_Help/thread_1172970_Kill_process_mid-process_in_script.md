---
title: "Kill process mid-process in script"
date: 2009-05-29
forum: General Help
---

### Post by AwesomeTux on 2009-05-29
So, I have this script...

```
zenity --text-info --editable --title "Text-to-Speech" --window-icon /usr/share/app-install/icons/kmouth.png --width 500 --height 300 > /tmp/tts-tmp.txt
festival --tts /tmp/tts-tmp.txt | zenity --question && killall -v festival
```

I want it to kill festival mid-process, after I click "OK", but it won't do it. Any help?

---

### Post by Carl H on 2009-05-29
Find the pid of festival with 

```
ps aux | grep festival
```

and then kill it (replace XXXX with the pid).

```
kill -9 XXXX
```

---

### Post by KyleBrandt on 2009-05-29
How about:
```

xcalc &; zenity --question && kill $!
```

$! is the pid of the last run job.

---

### Post by AwesomeTux on 2009-05-30
> **Carl H said:**
> Find the pid of festival with 

```
ps aux | grep festival
```

and then kill it (replace XXXX with the pid).

```
kill -9 XXXX
```

Didn't work. I have to have a way to stop the process while it's running. I.e. no command can be ran until the festival process is done.

I have to have a way to run the kill command at like a paused state, so when I press "OK" the kill command continues and kills the festival process.

---

### Post by AwesomeTux on 2009-05-30
> **KyleBrandt said:**
> How about:
```

xcalc &; zenity --question && kill $!
```

$! is the pid of the last run job.

Didn't work. As I said above. Nice try, though. I'll be using this for other things.

---

### Post by asmoore82 on 2009-05-30
would this work?```
zenity --text-info --editable --title "Text-to-Speech" \
   --window-icon /usr/share/app-install/icons/kmouth.png \
   --width 500 --height 300 > /tmp/tts-tmp.txt
festival --tts /tmp/tts-tmp.txt &
zenity --question && killall -v -INT audsp
```

& = run in background
audsp = festival seems to spawn these processes to do the talking
-INT = send SIGINT - the "ctrl+c" signal

---

### Post by AwesomeTux on 2009-05-30
> **asmoore82 said:**
> would this work?```
zenity --text-info --editable --title "Text-to-Speech" \
   --window-icon /usr/share/app-install/icons/kmouth.png \
   --width 500 --height 300 > /tmp/tts-tmp.txt
festival --tts /tmp/tts-tmp.txt &
zenity --question && killall -v -INT audsp
```

& = run in background
audsp = festival seems to spawn these processes to do the talking
-INT = send SIGINT - the "ctrl+c" signal

YOU THE MAN! It's working. Here is the currently working code...

```
zenity --text-info --editable --title "Text-to-Speech" --window-icon /usr/share/app-install/icons/kmouth.png --width 500 --height 300 > /tmp/tts-tmp.txt
festival --tts /tmp/tts-tmp.txt & zenity --question && killall -v audsp

```

Simple, nice, quick, hardly any dependencies. Change "festival" to "espeak" if you prefer. The only thing it needs is Zenity. I'm very happy with it. :D

---

