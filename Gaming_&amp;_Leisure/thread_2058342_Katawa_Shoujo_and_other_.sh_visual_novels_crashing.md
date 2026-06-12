---
title: "Katawa Shoujo and other .sh visual novels crashing"
date: 2012-09-15
forum: Gaming &amp; Leisure
---

### Post by tastefuldeath on 2012-09-15
Before I used 12.04, I was able to play visual novels with .sh files. When I reformatted and tried playing the same old files I have, the terminal turns on and then it dies instead of showing the visual novel. Any suggestions? I really wanna play Katawa Shoujo among other games hehe.

---

### Post by Sofox on 2012-09-15
> **tastefuldeath said:**
> Before I used 12.04, I was able to play visual novels with .sh files. When I reformatted and tried playing the same old files I have, the terminal turns on and then it dies instead of showing the visual novel. Any suggestions? I really wanna play Katawa Shoujo among other games hehe.

Open the Terminal and play the sh file from the terminal. Then, copy the output and paste it into a forum post.

If you have trouble running something from terminal, let us know.

---

### Post by tastefuldeath on 2012-09-15
I tried this. > kirsten@kirsten:~$ cd ~/Apps/KatawaShoujo-linux-x86/
kirsten@kirsten:~/Apps/KatawaShoujo-linux-x86$ chmod +x "Katawa Shoujo.sh"
kirsten@kirsten:~/Apps/KatawaShoujo-linux-x86$ sh "Katawa Shoujo.sh"
Katawa Shoujo.sh: 20: exec: ./lib/python: Permission denied
kirsten@kirsten:~/Apps/KatawaShoujo-linux-x86$ 


I have no idea what it means.

---

### Post by electricmaster on 2012-09-15
You have a problem with the file permissions. Try chmoding the Katawa Shoujo folder 777.  I know it's playable under 12.04 because I play that game all the time! ^^

---

### Post by tastefuldeath on 2012-09-15
> **electricmaster said:**
> You have a problem with the file permissions. **Try chmoding the Katawa Shoujo folder 777**.  I know it's playable under 12.04 because I play that game all the time! ^^

How do I do that? xD

Also, what could be the problem? This also happens to the other sh files I have.

I tried changing perms from the Apps folder and it doesn't stay changed. x___x It seems like the other folders I saved from my PC that I just transferred to Ubuntu are like this.

---

### Post by tastefuldeath on 2012-09-16
Thanks for leading me to have it fixed. xD I was able to change the perms woot woot. Working fine now.

---

