---
title: "Ubuntu 14.04 login loop - Guest sessions does not work either"
date: 2015-02-13
forum: Desktop Environments
---

### Post by Kaiyu_Zheng on 2015-02-13
[COLOR=#333333][FONT=UbuntuRegular]I have been using Ubuntu 14.04 soon after it is released. Today I messed something up with the Chinese input ibus, and I don't know if this is the reason at all, but when I reboot using sudo shutdown -r now, I cannot pass the login. I entered the correct password, but then the screen just went black, and then the login screen comes up again![/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
I have searched quite a few solutions from others, but nothing is working for me.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have read[/FONT][/COLOR]

[LIST]
[*][Ubuntu gets stuck in a Login Loop]("http://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop")
[*][ubuntu 14.04 stuck in login loop. Nothing seems to help]("http://askubuntu.com/questions/517794/ubuntu-14-04-stuck-in-login-loop-nothing-seems-to-help")
[*][Login screen loops unless you login as Guest]("http://askubuntu.com/questions/146137/login-screen-loops-unless-you-login-as-guest")
[*][What represent .Xauthority file?]("http://askubuntu.com/questions/300682/what-represent-xauthority-file")
[*]
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]I tried to look at .xsession-error, but that file is empty on my computer.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I tried the suggestion of changing the ownership of .Xauthority, but my .Xauthority is not root initially. I also tried to delete it but that does not work either.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I did sudo apt-get remove ibus-pinyin in case it is the problem (but not likely).
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I also tried sudo apt-get install --reinstall lightdm, but it does not work either. I also tried dpkg-reconfigure lightdm, but I was not able to see the effect.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Also, I looked at /var/crash, and I saw a file _usr_bin_xpad.1000.crash, which seems to record the crash occured at the time that I first encountered thr login loop problem. Yet I cannot find further clue of how to solve it. At the bottom of that file, it suggested to update several packages if the crash still occurs. I did so but it does not work either. These packages are krb5-locales, libgssapi-krb5-2, libk5crypto3, libkrb5-3, libkrb5support0, libprocps3, procps
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Can someone save me...I dont wanna switch back to Windows[/FONT][/COLOR]

---

### Post by grahammechanical on 2015-02-13
> [COLOR=#333333][FONT=UbuntuRegular] when I reboot using sudo shutdown -r now, I cannot pass the login.[/FONT][/COLOR]

Are you running that command in the terminal? Or a tty/console? Why are you not using Shut Down>Restart from the power cog menu?

If I use a tty to shut down, I must first login using my username and password. Then I can run 

```
sudo shutdown -r now
```

 and I will be required to enter my password.

Regards.

---

