---
title: "Cant Kill A Process"
date: 2009-05-20
forum: General Help
---

### Post by chipmunkproof on 2009-05-20
I am trying to manually stop a program called rejoystick because its messing up. Ive tried many things like kill and killall and I cant find the Id number. Im so confused please help!!! I want to play an emulator with a usb gamepad.

---

### Post by Bachstelze on 2009-05-20
```
ps aux | grep rejoystick
```

will tell you the PID of your process.

---

### Post by colau on 2009-05-20
> **chipmunkproof said:**
> I am trying to manually stop a program called rejoystick because its messing up. Ive tried many things like kill and killall and I cant find the Id number. Im so confused please help!!! I want to play an emulator with a usb gamepad.
```

ps aux | grep rejoystick
kill -9 <pid>

```

---

### Post by chipmunkproof on 2009-05-20
adam@adam-laptop ~ $ ps aux | grep rejoystick
adam      3614  0.0  0.0   3236   796 pts/0    S+   01:11   0:00 grep --colour=auto rejoystick
adam@adam-laptop ~ $ kill -9 3614
bash: kill: (3614) - No such process
adam@adam-laptop ~ $ kill -9 3236
bash: kill: (3236) - No such process
adam@adam-laptop ~ $ kill 3236
bash: kill: (3236) - No such process
adam@adam-laptop ~ $ kill 3614
bash: kill: (3614) - No such process


What Am I Doing Wrong?

---

### Post by t0p on 2009-05-20
```
pkill rejoystick
```

or alternatively, **System > Administration > System Monitor**, click the **Processes** tab and select it from the list.

---

### Post by regala on 2009-05-20
> **chipmunkproof said:**
> adam@adam-laptop ~ $ ps aux | grep rejoystick
adam      3614  0.0  0.0   3236   796 pts/0    S+   01:11   0:00 grep --colour=auto rejoystick


What Am I Doing Wrong?

there's no process called rejoystick
what is it ? a python script ? a perl script ? maybe it is called perl or python...

br, mathieu :)

---

