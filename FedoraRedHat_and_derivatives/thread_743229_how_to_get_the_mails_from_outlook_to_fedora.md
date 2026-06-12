---
title: "how to get the mails from outlook to fedora ?"
date: 2008-04-02
forum: Fedora/RedHat and derivatives
---

### Post by Auston on 2008-04-02
Hi all,

my system is a dual boot system on which both windows and fedora are installed now as outlook is generally used for mails but when i work on fedora i don't get the mails.

So how to configure mails on fedora so that i can get all mails coming to my outlook folder or my mail account.

[Ubuntu]("http://www.linux-archive.org/ubuntu/")

---

### Post by prshah on 2008-04-02
> **Auston said:**
> Hi all,
So how to configure mails on fedora so that i can get all mails coming to my outlook folder or my mail account.

I assume you mean Outlook Express?

In any case, in both Outlook and Outlook express, you have the option to export your account settings. Export them (you will land up with a .iaf file), boot into linux, open thunderbird and import the .iaf file.

HTH

---

### Post by cprofitt on 2008-04-05
If I am getting this correctly you want mail on both your windows and Fedora installs... if that is accurate you will need to select the option to leave the mail on the server -- if not when you get mail on one side you will not get it on the other because you will remove it from the server when you client 'receives' it.

---

