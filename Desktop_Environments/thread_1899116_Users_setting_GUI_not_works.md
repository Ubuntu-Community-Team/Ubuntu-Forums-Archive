---
title: "Users setting GUI not works"
date: 2011-12-22
forum: Desktop Environments
---

### Post by kholis on 2011-12-22
I try to add/modified user in Xubuntu. I open Applications > System > Users and Groups. But many button give no respons when I clicked on it. It almost give me no functionality at all. Only modified full name button is works.

This program called "users-admin" which part of "gnome-system-tools" package. 

Any clue? 

Note: I use Xubuntu 11.10

---

### Post by Toz on 2011-12-22
You need administrative privileges to make most of those changes. When you click on one of those buttons, a dialog box should pop up asking for your password so that you can gain those privileges. Are you getting this dialog box and are you entering in your password?

---

### Post by kholis on 2011-12-23
No, there is no dialog popup. 

I try it with "gksu users-admin" and with root privilege in terminal but its became hangs. Mouse keep spinning around waiting for program loaded. Click on [X] button in xfwm won't close this program, i have to kill it in terminal

[https://picasaweb.google.com/110272637166329645837/Misc#5689168874439149090]("https://picasaweb.google.com/110272637166329645837/Misc#5689168874439149090")

---

### Post by Toz on 2011-12-23
When you try with root privilege in terminal, do you get any messages in the terminal?

What is contents of your /etc/hosts file? Have you made any changes to that file?

Can you run the following test and post back the results:
```
sudo -K; gksudo -d echo Test
```

---

### Post by kholis on 2011-12-23
> **Toz said:**
> When you try with root privilege in terminal, do you get any messages in the terminal?

nope. no message at all.

> **Toz said:**
> 
What is contents of your /etc/hosts file? Have you made any changes to that file?

Here is my hosts file. I never made any changes on that:

```
127.0.0.1	localhost
127.0.1.1	kalau.solusi247.com kalau
192.168.5.136	kalau.solusi247.com kalau

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```


> **Toz said:**
> Can you run the following test and post back the results:
```
sudo -K; gksudo -d echo Test
```
Here is the output
```

No ask_pass set, using default!
xauth: /tmp/libgksu-NhsHIY/.Xauthority
STARTUP_ID: gksudo/echo 'Test'/16818-0-kalau_TIME18943833
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: echo
cmd[9]: Test
buffer: -GNOME_SUDO_PASS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
Test
xauth: /tmp/libgksu-NhsHIY/.Xauthority
xauth_env: /home/kholis/.Xauthority
dir: /tmp/libgksu-NhsHIY

```

---

### Post by Toz on 2011-12-23
> **kholis said:**
> nope. no message at all.


Here is my hosts file. I never made any changes on that:

```
127.0.0.1	localhost
127.0.1.1	kalau.solusi247.com kalau
192.168.5.136	kalau.solusi247.com kalau
```
Try removing the domain from your localhost name:
```
127.0.0.1	localhost
[COLOR="Red"]127.0.1.1	kalau[/COLOR]
192.168.5.136	kalau.solusi247.com kalau

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
> Here is the output
```

No ask_pass set, using default!
xauth: /tmp/libgksu-NhsHIY/.Xauthority
STARTUP_ID: gksudo/echo 'Test'/16818-0-kalau_TIME18943833
cmd[0]: /usr/bin/sudo
cmd[1]: -H
cmd[2]: -S
cmd[3]: -p
cmd[4]: GNOME_SUDO_PASS
cmd[5]: -u
cmd[6]: root
cmd[7]: --
cmd[8]: echo
cmd[9]: Test
buffer: -GNOME_SUDO_PASS-
brute force GNOME_SUDO_PASS ended...
Yeah, we're in...
Test
xauth: /tmp/libgksu-NhsHIY/.Xauthority
xauth_env: /home/kholis/.Xauthority
dir: /tmp/libgksu-NhsHIY

```
Did the dialog box popup asking for your password?

---

### Post by wkrekik on 2011-12-23
Have you disabled some program from autostart ? I have had the same problem when I disabled some gnome stuff from autostart (gnome keyring or so on, I forgot) to reduce RAM usage, and that prevented root access in some applications.

---

### Post by kholis on 2011-12-25
> **Toz said:**
> Did the dialog box popup asking for your password?
Yup.

> **wkrekik said:**
> Have you disabled some program from autostart ? I have had the same problem when I disabled some gnome stuff from autostart (gnome keyring or so on, I forgot) to reduce RAM usage, and that prevented root access in some applications.

Bingo! once I re-enable gnome-keyring (gpg, pkcs11, secret and ssh) and PolicyKit Authentication Agent in xfce autostart, everything goes fine now. :)

Thank you very much wkrekik.

---

### Post by AlexandreMBM on 2013-02-21
See ["Re: NX Server, policykit, remote privileges" #3]("http://ubuntuforums.org/showpost.php?p=10095159&postcount=3") as analogy.

Try to edit the /usr/share/polkit-1/actions/org.freedesktop.accounts.policy file.

---

### Post by wildmanne39 on 2013-02-21
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

