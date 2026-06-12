---
title: "sudo doesn't work"
date: 2006-03-30
forum: Desktop Environments
---

### Post by grylliade on 2006-03-30
Alright, I've looked everywhere and I can find no solution to this; perhaps someone here will have some ideas. Every time I try to do anything that requires sudo, I'm asked for my password. I put it in, and nothing happens. No matter what I try to run, nothing happens. For fifteen minutes, I can try to run anything that requires sudo, and it won't ask me for my password, but it still won't run. I tried "sudo -s" from a console; it asked me for my password, I gave it, and nothing happened. The prompt was still "$" instead of "#". I can't even install updates until / unless I get this fixed. I like Ubuntu, but if I can't get this fixed I (obviously) won't be able to use it. Any help, any suggestions, would be greatly appreciated.] (*,)

---

### Post by 5-HT on 2006-03-30
Is this a new install, or has sudo previously worked?
If it's a new install, you didn't happen to do an 'expert install' did you?
I know that the expert install does not add the user you created during the install to the 'sudoers' file.

This file is what determines who can/can't use sudo, as well as what they can/can't use it for.

Even if you didn't perform the expert install, most likely your sudoers file is whats causing the problem.


Here is a great post from Mustard that describes how you can add your user to the sudoers file.
[http://ubuntuforums.org/showpost.php?p=860170&postcount=4]("http://ubuntuforums.org/showpost.php?p=860170&postcount=4") 

(Original thread: [http://ubuntuforums.org/showthread.php?t=150021&highlight=sudoers]("http://ubuntuforums.org/showthread.php?t=150021&highlight=sudoers"))

You basically need to boot into single user mode so you can become root, and then add your user to the sudoers file. Mustard's post is a great walkthrough of the process.

Hope this helps.

---

### Post by grylliade on 2006-03-30
[I]Is this a new install, or has sudo previously worked?
If it's a new install, you didn't happen to do an 'expert install' did you?
I know that the expert install does not add the user you created during the install to the 'sudoers' file.[/I]

Yeah, I did an expert install, even though I'm nowhere near an expert Linux user (obviously). After I posted this, there were links to similar threads at the bottom, which contained the solution. Of course. It was just that my regular account wasn't in the sudoers file. Thanks for the advice, and prompt response!

---

