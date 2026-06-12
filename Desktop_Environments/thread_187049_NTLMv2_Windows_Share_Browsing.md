---
title: "NTLMv2 Windows Share Browsing"
date: 2006-06-02
forum: Desktop Environments
---

### Post by Yi Ding on 2006-06-02
Hi Guys,

My first time on these forums.  First off, I'd like to say that this is the most polished Linux release I've used so far, with things like wireless, suspend, and hibernate working perfectly on my laptop.

However, I have a question about browsing a Windows share.  My institution uses NTLMv2 authentication only, so I added a line to my smb.conf file
```
client ntlmv2 auth = yes
```
Now, smbclient works for me perfectly.  However, when I try to connect to the server using the places menu in GNOME, it asks me for the password repeatedly and cannot connect.  Is there a setting so that I can set change that to also use NTLMv2 authentication?

---

### Post by iansyngin on 2007-05-18
Good Question.
I'm currently experiencing the same problem. Our Exchange Server requires NTLM V2 authentication also. I'm unable to use the Exchange feature of Evolution because of this i think.
Anyone have similar issues?

---

