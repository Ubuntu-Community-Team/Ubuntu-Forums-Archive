---
title: "Problems with tee"
date: 2009-05-07
forum: General Help
---

### Post by alphaniner on 2009-05-07
I haven't used tee in a while, but I'm pretty sure it's not working right.  When I use it with a command that takes time and makes numerous updates to the screen, specifically '7za t file.7z |tee /tmp/output', it hangs.  After running the command, it will hang with a blinking cursor, then spit out a bunch of lines to the screen.  Based on the filename it is usually about 75% through the archive by time I get the first spurt.  Moreover, the last line in a spurt is usually cut off part way.  For example, it stops at

```
Testing     fil
```

when the full line would be

```
Testing     filename
```

The line gets completed in the next spurt.  It usually get one or two spurts before the before the command completes.  When I run the command without tee, the output comes as expected, ie. a line as each file is tested.

I also tried 'find / -name *.sh |tee /tmp/output' - to verify that it wasn't related to the 7zip command - and saw the same behaviour.  I know the output of find doesn't exactly come at a predictable pace, but there shouldn't be cut off lines.  I've tried moving the archive to a different HDD before testing, and redirecting the output to another HDD.  I also tried running it on a real terminal rather than xterm.  That's about the only troubleshooting I could come up with aside from trying it on a different PC, which is not an option at this time.  So any input or suggestions would be greatly appreciated.

---

### Post by lensman3 on 2009-05-08
The cutoff lines could be an artifact of the terminal.  Does the terminal have line wrap on.  Also from your example, you probably could get away with "more" except the /tmp file wouldn't be created.  

try:

7?? <filename | tee /tmp/output | more 

change more to "cat". See if that works better. "cat" has an end-of-line mode that prints a $ at the EOL.  Also try the "tail -f" command.  Since these are all pipes, I don't think there is any way to control how fast the pipe is filled or how fast it is emptied.

After that try "stty" and turn n the flush immediately flag, if there is one!

---

### Post by alphaniner on 2009-05-08
The commands you suggested didn't change the behaviour, but your mention of how fast pipes are filled and emptied was most helpful.  I figured pipes would be filled and emptied immediately.  So I went back and ran the initial command (7za t file.7z |tee /tmp/output) and then immediately opened up a new tab.  There I ran 'tail -f /tmp/output', which output nothing.  I opened up another tab and did 'ls -l /tmp/output', which showed the file at 0B.  I kept checking and the file stayed at 0 B for around four minutes then suddenly jumped to 4096 B.  After the jump, the other two tabs had printed out the information.

I searched the stty manpage for flush but didn't discover anything useful.  I'll probably make a new post on a broader forum.  Nevertheless, thank you so much for putting me on the right track!

---

