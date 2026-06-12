---
title: "Small business environment"
date: 2021-04-14
forum: Desktop Environments
---

### Post by jag77202 on 2021-04-14
We are a small business with about 28 computers. Most are all home windows operating system My interest is to reload all of the computers with Linux and start a business environment with our Network.

I like to have something like Microsoft's active directory for authentication tree with the desktops without using Microsoft 

All of the computers only use Libre office and a browser some some use gimp so moving away from Microsoft is simple yet I'd like to have an account controlled for one Authentication

Under Linux/Ubuntu does this exist?

---

### Post by CelticWarrior on 2021-04-14
Welcome.

I suggest you start by googling and understanding about Kerberos/LDAP (and Debian/Ubuntu).
Then feel free to post your questions/doubts.

---

### Post by rsteinmetz70112 on 2021-04-14
The free open source Samba Suite can provide a Active Directory Domain Controller which can do the authentication for Windows and Linux. It also does windows file and printer sharing. It is mostly used in environments when you have Windows clients which you wouldn't have in you scenario.

Kerberos/LDAP can do the authentication in a purely Linux environment. File sharing in Linux would work best with NFS the native Unix/Linux file sharing system.

For starters I'd set up a single Ubuntu server and get LDAP/Kerberos working. Then converting the desktops and joining the network will be relatively straightforward.

---

### Post by ActionParsnip on 2021-04-15
I'd go LDAP but if you want authentication for both then you can use Windows AD.

---

### Post by mIk3_08 on 2021-08-10
> **jag77202 said:**
> We are a small business with about 28 computers. Most are all home windows operating system My interest is to reload all of the computers with Linux and start a business environment with our Network.
I like to have something like Microsoft's active directory for authentication tree with the desktops without using Microsoft
All of the computers only use Libre office and a browser some some use gimp so moving away from Microsoft is simple yet I'd like to have an account controlled for one Authentication
Under Linux/Ubuntu does this exist?
Wow! This is cool. Just want to remind you that Linux is not Microsoft.
But If the Internet Cafe' is for Gaming/ Entertainment purposes and you are from Philippines; I won't recommend to use Linux;
Mostly from Philippines uses Microsoft for Internet cafe's for games and etc. 

1st. Microsoft can run a lot of Local Games specially new one.
2nd. Microsoft has also a lot of Software Applications. PS, CAD and etc. which is very popular and has also a big contribution to the world already. (Software Applications are more Friendly) 
3rd. Microsoft (Here in Philippines) is already known as user Friendly Operating System; Easy to use specially to the Software Application Tools. (GUI Based)
4th. Microsoft is best for Kids. Here in Philippines, Internet cafe's most users are Kids. 
5th. Microsoft is best in GUI Based and More Friendly
6th. Microsoft is design for GUI based small data. (Not same as Linux)

1st. Linux can run limited local games (Though there are already a lot of old games that run here on Linux but not as compared to Microsoft)
2nd. Linux has limited on Software Application (Though there are some same application software in Windows but not as friendly as Microsoft Software Applications) (Command Line Based Application Tools.)
3rd. Linux Operating System here in Philippines only few knows it. 
4th. Linux is best on Development Skills via Web. Not as friendly as Microsoft. Not that friendly for kids.
5th. Linux is a Command Line Based (Not that the same as Microsoft GUI Based) Linux is best for security purposes. Very powerful on clouds. (Command Line Based Application Tools.)
6th. Linux is design for handling a Large Data. (Command Line Based Application Tools.)


If I where you; you better run it for code studies if you don't have any idea to use it via web interfacing.
Its just same as you are riding a bicycle; if you don't know how to ride a bicycle you definitely fall but if you will study how to ride a bicycle; definitely you will succeed.

---

