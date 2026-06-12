---
title: "reading output while it is being created"
date: 2009-03-16
forum: General Help
---

### Post by cybo on 2009-03-16
i dump my output to the file. i need to be able to see the output file while the file is being updated. i was shown a command once how to do it but i can't remember it.

it has something to do with

tail <some option> <filename>

does anyone know what i'm talking about?

---

### Post by heindsight on 2009-03-16
The command you're looking for is tee.

Use it like:
```
somecommand | tee file
```
Then the output of somecommand will be sent to the tee command, which will simultaneously write it to the screen and to file.

---

### Post by albandy on 2009-03-16
tail -f filename

---

### Post by cybo on 2009-03-16
tail -f filename, that is what i was looking for. thank you albandy

---

### Post by heindsight on 2009-03-16
OK, I think I may have misunderstood.

If you have some command that usually prints it's output to the terminal and you want that output sent to a file while at the same time seeing the output on screen, then use the tee command as I posted before.

If you have a command that just sends output to a file, and you want to see the data on screen as it's being written to the file, then use tail as [albandy]("http://ubuntuforums.org/member.php?u=715896") pointed out.

---

