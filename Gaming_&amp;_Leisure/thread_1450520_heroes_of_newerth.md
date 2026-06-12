---
title: "heroes of newerth"
date: 2010-04-09
forum: Gaming &amp; Leisure
---

### Post by rexwesker on 2010-04-09
yup..i downloaded it and i cant install it..when i run this .sh file it crashes..and thats all tnxx

---

### Post by ELD on 2010-04-09
Well that was helpful...

You need to actually give us a bit more information. Like what was the error, did you try running it in terminal to see an error? etc etc...use your head we can't help you if you give us nothing.

---

### Post by rexwesker on 2010-04-09
theres nothign at all..double click it,run in terminal.nothing happens..so sorry

---

### Post by dyltman on 2010-04-09
> **rexwesker said:**
> theres nothign at all..double click it,run in terminal.nothing happens..so sorry

you need to make it executable, go to properties - permissions (I think) - Allow executing as a program (Once again I think)

---

### Post by donkyhotay on 2010-04-09
> **rexwesker said:**
> theres nothign at all..double click it,run in terminal.nothing happens..so sorry

:rolleyes: Then what's the output from the terminal? If the terminal screen immediately closes afterwards, load up the terminal first then run from terminal to get the output. If you're looking for help then help us, help you. Now if you're not wanting help and just want to complain then try posting to /dev/null instead since it'll have the same result without wasting everybody's time.

---

### Post by rexwesker on 2010-04-10
wesker@wesker-45:~$ cd /home/wesker/Desktop/
wesker@wesker-45:~/Desktop$ ./HoNClient-0.3.1.sh
156200+0 records in
305+1 records out
156200 bytes (156 kB) copied, 0.107648 s, 1.5 MB/s



PANIC
  Initial setup failed. Cannot continue.

thats it

---

### Post by Xorlathor on 2010-04-27
> **rexwesker said:**
> wesker@wesker-45:~$ cd /home/wesker/Desktop/
wesker@wesker-45:~/Desktop$ ./HoNClient-0.3.1.sh
156200+0 records in
305+1 records out
156200 bytes (156 kB) copied, 0.107648 s, 1.5 MB/s



PANIC
  Initial setup failed. Cannot continue.

thats it

Does anyone know a fix for this? I have the exactly same problem and don't know what to do...

---

### Post by got awesome? on 2010-04-28
I just installed it without a hitch. Be sure to make the file executable, either with "chmod +x yourHoNfile.sh" in the terminal, or right click >> properties >> permissions and tick the Execute box.

It's isn't executable by default.

---

### Post by myromance123 on 2010-04-28
Just to point it out, you guys aren't using the correct syntax when you run it from the terminal.

Don't do this:
> ./HoNClient-0.3.1.sh

And don't do this:
> robert@robert-laptop:~$ '/home/robert/Downloads/HoNClient-0.3.3.1.sh' 

Instead do this:
```
sh HoNClient-0.3.1.sh
```

Just make sure you're in the right directory (the one where the installer is in).

You could also do it with the GUI method. That way you won't make any mistake. Below is how.

First right click your installer. Then go to Properties.
Now, click the Permissions tab. Near the bottom is a tick-able box that says "Allow executing file as program". Tick it.
Then press Close.
Now double click HoNClient-0.3.1.sh.
A window should pop-up asking,
> Do you want to run "HoNClient-0.3.1.sh", or display its contents?
Out of the four click-able buttons, click Run.
The installer should then start up without a problem.

Let us know if that still doesn't work.

---

### Post by HaCkm4n on 2010-04-28
> **got awesome? said:**
> I just installed it without a hitch. Be sure to make the file executable, either with "chmod +x yourHoNfile.sh" in the terminal, or right click >> properties >> permissions and tick the Execute box.

It's isn't executable by default.


what he said. this worked for me. i did the GUI approach. righclick++

---

