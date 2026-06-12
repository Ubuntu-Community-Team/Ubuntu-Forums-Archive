---
title: "backgrounding a linux command without the ampersand"
date: 2009-03-11
forum: General Help
---

### Post by shyft on 2009-03-11
I ran in to this problem while connected to an ssh session at work.

I was transferring several large files with scp.

Can I background a process without halting/pausing it altogether?

I use ampersands all of the time when I know that I will be doing something else, but what of the moments when I don't expect to need that process in the background.

I understand that CTRL+Z suspends the program, but I want it to continue even after I press CTRL+Z.

Let's say that I am wget-ing some iso, and I all of a sudden want to pop open nano or vim without affecting my download.

I see no reason this couldn't be implemented if it's not already.
rather than pause, continue running...
the process could still show up in the jobs list

I have read that some folks use gnu screen to workaround this problem, but, I would still need to know that I needed it beforehand.

any input or suggestions?

-shyft

---

### Post by gersongarcia on 2009-03-11
Dear shyft,

Why can't you just open another terminal window to run your nano or vim? Why you need to move from background to foreground?

But to answer your question, you can do:

# cat loop.sh
while [ TRUE ]
do
        sleep 5
done

#./loop.sh&
[1] 19156
# jobs
[1]+  Running                 ./loop.sh &
root@ubuntu:/test# fg 1
./loop.sh
CTRL-Z
[1]+  Stopped                 ./loop.sh
# jobs
[1]+  Stopped                 ./loop.sh
# bg 1
[1]+ ./loop.sh &
# jobs
[1]+  Running                 ./loop.sh &
# fg 1
./loop.sh
CTRL-C
#

Use job control to move process from background to foreground and vice-versa.

---

### Post by shyft on 2009-03-16
thanks for your solution, but i would need to know that i would be multitasking, and if i knew i would just start it in the background.

The reason it came up originally, was because i was ssh'd into a machine at work and i unexpectedly wanted to do something else on that machine while the file transfer continued.

i cant open another terminal because there is no gui. i dont know if you can do ctrl-alt-f3 in an ssh session.

i just tried scp'ing a file, then hitting ctrl-z, fg, and so-on and that transfer seems to have kept running in the background.

however, a wget transfer did not.

i dont suppose there is a way to do what i want.

but thanks for your help.
-shyft

---

