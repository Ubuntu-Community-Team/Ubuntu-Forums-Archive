---
title: "KDE Daemon request password at every login"
date: 2009-04-24
forum: Desktop Environments
---

### Post by christoforever on 2009-04-24
Yes its just that. Everytime i log into the desktop, KDE Daemon requests a password even though i set it allow-always? Any ideas?

---

### Post by benerivo on 2009-04-24
It might be a startup program, that requires a password. What do you have startup automatically? An example might be the wireless network manager that starts in the system tray.

---

### Post by christoforever on 2009-04-24
As far as I know just the wireless network manager. This is my first round with Kubuntu after using Ubuntu for the past couple of years so I'm still getting the hang on how things work and where they are. But yes I don't have any special startup scripts nor did I add any extra programs to start up.

---

### Post by benerivo on 2009-04-25
It sounds like it might be the networkmanager, which is started automatically in kubuntu through the plasma-widget-network-manager. It requires keyring authentication to try to connect to a signal.

(I dont use networkmanager myself, as i find wicd to be a better option for me. You could try wicd by just installing the package, and it should remove networkmanager and make wicd startup automatically.)

I'm not sure how to get networkmanager to access the keyring automatically, but i have heard about the problem. See here for more info...[http://www.google.com/search?hl=en&client=iceweasel-a&rls=org.debian%3Aen-US%3Aunofficial&q=network-manager+startup+password&btnG=Search](http://www.google.com/search?hl=en&client=iceweasel-a&rls=org.debian%3Aen-US%3Aunofficial&q=network-manager+startup+password&btnG=Search)I think the problem is based on the default keyring not being open and available to packages when ubuntu is started.

---

### Post by christoforever on 2009-04-25
After playing with it for a while I just gave up. How kde and the wallet and the network manager work together seems very buggy at the moment. So I installed wicd..... Awesome. It does everything that it's suppose too, easy to use and connects to networks even before the desktop is loaded. Thanks for the heads up on wicd.

---

### Post by BDNiner on 2009-08-05
No one has come up with a solution to this issue except for uninstalling network manager and using wicd?

---

### Post by sk1887 on 2010-10-11
> **BDNiner said:**
> No one has come up with a solution to this issue except for uninstalling network manager and using wicd?

There is still this problem in kubuntu 10.10.. crazy . I think I will try to delete the keyring. On Ubuntu this problem happens when you have auto login active, but on Kubuntu happens with normal login.

---

### Post by ankspo71 on 2010-10-11
Hi,
I'm not using my Kubuntu at the moment so my advice might be a little off. Open your KDE network manager and look around for a "Connection Secrets" setting. When you find it, choose "In File (Unencrypted)". You may have to enter your password to make this change. After you make this change the network manager will stop asking you for a password on startup.

---

### Post by Paki on 2010-11-28
I'm having this same problem with KDE Daemon at log-in, but I do know that a solution has been found to the problem with Network Manager. Indeed, I used this solution and it shifted my problem from being with Network Manager needing a password every log-in to KDE Daemon needing a password at every log-in. See: [http://ubuntuforums.org/archive/index.php/t-1268434.html](http://ubuntuforums.org/archive/index.php/t-1268434.html)

---

### Post by Simian Man on 2010-11-28
Sounds like it might be the KDE Wallet system.  Go into the KDE settings and disable the KDE Wallet.

---

### Post by Paki on 2010-11-28
That's what I've ended up doing, but I think it's pretty lame that I can only have my passwords stored in an encrypted file at the cost of having to effectively log in to my user account twice; once is enough.

---

### Post by cooljel on 2011-05-22
To work around the problem.
I set the kdewallet a blank password.

---

### Post by Droopy_Snowmen on 2012-03-23
I know this thread is almost a year old, but I'm sure this is a recurring problem, as I have experienced it with NetworkManager on several distros using several window environments.

Thankfully, the problem seems to go away if open network manager settings, and edit the connection that is trying to start on login. There should be a checkbox somewhere that says something like "System connection" or "Only for this user."

Basically, you want to select or deselect that checkbox in order to make the connection system-wide. This means any user can connect using that connection, but it also seems to solve the wallet issue.

---

