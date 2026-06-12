---
title: "Which COM port is my CM11A attached to?"
date: 2009-05-15
forum: General Help
---

### Post by Maheriano on 2009-05-15
I compiled and installed Heyu to run my X10 stuff but it asks me which port my CM11A is attached to. I have it hooked up via a serial PCI card but it's asking me if it's ttyS0, ttyS1 or something different. How do I know?

Here's what I got when I guessed ttyS0 on the install and tried to run a command:

```
deemar@Chugger:~/Desktop/heyu-2.6.0$ heyu info
Invalid status response (was 0 bytes instead of 14)
HEYU: No response from the CM11A on /dev/ttyS0
Program exiting.
```

---

