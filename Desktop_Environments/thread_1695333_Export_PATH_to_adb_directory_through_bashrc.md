---
title: "Export PATH to adb directory through bashrc"
date: 2011-02-25
forum: Desktop Environments
---

### Post by Cypher2 on 2011-02-25
Hello :)

I,m having a rough time getting the terminal environment to recognize my android debug bridge path (which is set in a separate hdd)

I used to paste this in my bashrc, but then found that it would make the env system bonkers whenever i attempted sudoing with an option:

# Android Debug Bridge (ADB) sdk path
alias sudo='sudo env PATH=$PATH'
export PATH=${PATH}:/media/Disk/Linux/Android/sdk/platform-tools/

The "alias" line was the one making me have a rough time with env.

Now that i got rid of it everything is well but adb's path isn't exported anymore.

Here's the output when I call an adb command:


bash: /media/Disk/Linux/Android/sdk/platform-tools/adb: No such file or directory

Another forum guiding Ubuntu users (maverick specifically) does not use any other strategy, other than bashrc, which I've tried, their way, without any success...

Link: [http://forum.xda-developers.com/showthread.php?t=820122](http://forum.xda-developers.com/showthread.php?t=820122)

Help?

---

### Post by -AmazingLarry- on 2011-03-03
have you checked ownership on your /media folder?

---

### Post by gsgleason on 2011-03-03
'which adb'
'alias adb'

please show output of those.

---

### Post by dasunsrule32 on 2011-03-16
> **Cypher2 said:**
> Hello :)

I,m having a rough time getting the terminal environment to recognize my android debug bridge path (which is set in a separate hdd)

I used to paste this in my bashrc, but then found that it would make the env system bonkers whenever i attempted sudoing with an option:

# Android Debug Bridge (ADB) sdk path
alias sudo='sudo env PATH=$PATH'
export PATH=${PATH}:/media/Disk/Linux/Android/sdk/platform-tools/

The "alias" line was the one making me have a rough time with env.

Now that i got rid of it everything is well but adb's path isn't exported anymore.

Here's the output when I call an adb command:


bash: /media/Disk/Linux/Android/sdk/platform-tools/adb: No such file or directory

Another forum guiding Ubuntu users (maverick specifically) does not use any other strategy, other than bashrc, which I've tried, their way, without any success...

Link: [http://forum.xda-developers.com/showthread.php?t=820122](http://forum.xda-developers.com/showthread.php?t=820122)

Help?

You need to call the alias after you create the PATH. ;) So:
```

export PATH=$PATH:/media/Disk/Linux/Android/sdk/platform-tools
alias sudo='sudo env PATH=$PATH'

```

Verify that the drive is mounted:
```

mount|grep -i media

```

---

