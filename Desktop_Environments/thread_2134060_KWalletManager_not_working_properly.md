---
title: "KWalletManager not working properly"
date: 2013-04-10
forum: Desktop Environments
---

### Post by elefant23 on 2013-04-10
Hi folks,

Since couple of days a ago, I'm having problem with KWalletManager/kdewallet. It's strange behavior includes:
[LIST]
[*]Choqok which uses the wallet says I have no account setup (which I have several accounts and have been using it properly for long period).
[*]Kontact which also uses the wallet has problem connecting to IMAP accounts.
[*]Every time I start apps that uses the wallet, I get prompted to input master password of the wallet.
[*]After struggling with above problem for couple of days, I deleted kdewallet (default wallet that would be made). When I start apps uses the wallet, KWalletManager/kdewallet still keeps asking me for password.
[*]After deleting kdewallet, I try to create another kdewallet. I enter it's password to create new master password  (and they match), but a new kdewallet does not appear in KWalletManager.
[*]Since then, the screen that prompts for two passwords (the one that appears when creating a new wallet) every time I start apps that uses KWalletManager/kdewallet (e.g., Choqok).
[/LIST]
Please note that passwords including master password are all correct. 
Also, /home/<user name>/.kde/share/apps/kwallet/ does not exist.
I need to be able to use Kontact and Choqok.
My OS is Ubuntu 12.10. I installed KDE SC, and I often use KDE.

Any thoughts? Has anyone experienced similar problems? Any helps/suggestions/hints/links are welcome. Thanks in advance!

---

### Post by elefant23 on 2013-04-11
Hi folks,

So here is my update:
[LIST]
[*]After deleting and re-creating kdewallet (by using both GNOME and KDE), "~/.kde/share/apps/kwallet/kdewallet.kwl" does exist now.
[*]However, I still experience strange behavior of KWalletManager/kdewallet.
[*]In GNOME, apps such as Kontact and Choqok can access kdewallet w/o any problems. They work perfectly fine.
[*]In KDE. I launch KWalletManager and try to open kdewallet, but the content of kdewallet is empty. In the window of "kdewallet," I should be seeing "Forms" and the like under "Folders." Kontact and Choqok have problem accessing my account information.
[/LIST]

Folks and experts, do you have any good thoughts what I can do? Am I seeing this problem due to KWalletManager alone or combination of KDE SC? Any suggestions/thoughts/help/links/ideas are most welcome. Thanks very much in advance!

---

### Post by levi dehaan on 2013-04-20
The same is happening to me.
It happened on my last install 12.04 -distupgraded-> 12.10
i deleted my wallet all the same things, that never fixed it.

I have a wallet that just pops up, I am putting in the right password, however it just keeps asking. This is for the KNetwork Manager. however when i go to the wallet manager, it wont actually open the wallet.
it wont give me an error, i can put in any password i want and kwallet manager just opens up like its a good password, but no menu's are usable.

I just installed a fresh copy of 13.04 and its the same thing, i put in my wallet password when i first booted up and logged into my wifi network.
now every time i reboot I have to delete the wireless entry from Knetwork manager and redo it.

I've disabled KWallet, but I would rather not.
has anyone discovered a solution to this issue.

Deleting wallets does not work btw
it will create a new one and ask for the password, but that password will Not work.

---

### Post by Cerealklr on 2013-06-15
Bump. This is a new issue for me as of updating to 13.04. I'd be happy to provide any debug information that might be relevant. This is a real pain since some widgets and apps will not work without the wallet subsystem enabled.

---

### Post by FreeMinded on 2013-08-24
Hi all,

Since the update to KDE 4.11 I face the same issue. KWallet wont open anymore.
Any solutions yet?

---

### Post by FreeMinded on 2013-08-24
Hi all,

Since the update to KDE 4.11 I face the same issue. KWallet wont open anymore.
Any solutions yet?

Update:
Upps, sorry for double posting. Admins, please delete this post if possible.

---

### Post by bra|10n on 2013-08-24
[http://www.kubuntuforums.net/showthread.php?61877-Resetting-Kwallet](http://www.kubuntuforums.net/showthread.php?61877-Resetting-Kwallet)

---

### Post by FreeMinded on 2013-08-25
> **bra|10n said:**
> [http://www.kubuntuforums.net/showthread.php?61877-Resetting-Kwallet](http://www.kubuntuforums.net/showthread.php?61877-Resetting-Kwallet)

I tried that but it doesn't work. Instead of constantly asking me for the password to open KWallet it's now asking for a password to create a new KWallet (even if I try to open an existing one. But whatever I try it never gets created.

Running from konsole it get this:
```
user@computer:~$ kwalletmanager 
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
user@computer:~$
```

Is that of any help solving the issue? Google hasn't been much of a help so far.

---

### Post by bra|10n on 2013-08-25
System Settings > Account Details > KDE Wallet
Have you checked kwallet is enabled and the settings haven't been changed inadvertently by the updates?

---

### Post by FreeMinded on 2013-08-25
> **bra|10n said:**
> System Settings > Account Details > KDE Wallet
Have you checked kwallet is enabled and the settings haven't been changed inadvertently by the updates?

Yes, I checked that and everything looks right. It's really KWallet who has an issue opening the wallet. But why???

---

### Post by FreeMinded on 2013-08-25
I just found out that deactivating it in the System Settings > Account Details > KDE Wallet and reactivating it fixes it for the running session. After each reboot it fails again.
You may also see this bug report [https://bugs.kde.org/show_bug.cgi?id=322562](https://bugs.kde.org/show_bug.cgi?id=322562)

Update: I have created a new bug report on Kubuntu PPA: [https://bugs.launchpad.net/kubuntu-ppa/+bug/1216618](https://bugs.launchpad.net/kubuntu-ppa/+bug/1216618)

---

### Post by bra|10n on 2013-08-25
> **FreeMinded said:**
> Yes, I checked that and everything looks right. It's really KWallet who has an issue opening the wallet. But why???

I have installed KWallet to try this which gave me the same dbus errors as yours when trying to launch it from the menu.

Try **sudo kwalletmanager** and re-check your settings.

In particular, Access control in the second tab in KDE Wallet Configuration (Prompt...). 
Remember you are running KWallet as root for the time being...
Now close down all instances of KWallet and check its not still open in the systray also.

Here, after doing the above KWallet starts from the menu (opens in the systray).

I appreciate yours and my situations are a little different to begin with but you might just have some luck with this share.

```
$ bool DBusMenuExporterDBus::AboutToShow(int): Condition failed: menu 
bool DBusMenuExporterDBus::AboutToShow(int): Condition failed: menu 
bool DBusMenuExporterDBus::AboutToShow(int): Condition failed: menu 
uint DBusMenuExporterDBus::GetLayout(int, int, const QStringList&, DBusMenuLayoutItem&): Condition failed: menu 
uint DBusMenuExporterDBus::GetLayout(int, int, const QStringList&, DBusMenuLayoutItem&): Condition failed: menu 
uint DBusMenuExporterDBus::GetLayout(int, int, const QStringList&, DBusMenuLayoutItem&): Condition failed: menu 
bool DBusMenuExporterDBus::AboutToShow(int): Condition failed: menu 
bool DBusMenuExporterDBus::AboutToShow(int): Condition failed: menu 
bool DBusMenuExporterDBus::AboutToShow(int): Condition failed: menu 
bool DBusMenuExporterDBus::AboutToShow(int): Condition failed: menu 
bool DBusMenuExporterDBus::AboutToShow(int): Condition failed: menu 
bool DBusMenuExporterDBus::AboutToShow(int): Condition failed: menu 


```

---

