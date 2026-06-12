---
title: "Will a ubuntu linux server actually be able to IUSE a windows DNS server?"
date: 2009-01-19
forum: General Help
---

### Post by Linuxwho? on 2009-01-19
I mean "use" not IUSE"  sorry.  Like after entering the proper DNS in "resolv.cfg" file for example?  Are there an communication gaps or other configs required?  Any other links or sources to linux systems communicating with windows stuff?  Thanks.

---

### Post by hyper_ch on 2009-01-19
there shouldn't be any issue. Request for dns info is a protocol which should be (and hopefolly also is) OS-independant. You'd just tell your linux box that the server with IP xxx.xxx.xxx.xxx is the nameserver to be queried for dns stuff.

---

