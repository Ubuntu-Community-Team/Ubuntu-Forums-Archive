---
title: "download file"
date: 2009-05-26
forum: General Help
---

### Post by m_adel on 2009-05-26
hi..
i am trying to download this file:
[http://nogomi.com/download.asp?cat=mp3&ID=1700](http://nogomi.com/download.asp?cat=mp3&ID=1700) 

using wget :

```

wget --user=<MyaccountName> --password=<MyPassword>  http://nogomi.com/download.asp?cat=mp3&ID=1700

```

this error apears:

Resolving nogomi.com... 93.174.93.202
Connecting to nogomi.com|93.174.93.202|:80... connected.
HTTP request sent, awaiting response...**[COLOR=Red] 500 Internal Server Error[/COLOR]**
**[COLOR=Red]2009-05-26 08:19:07 ERROR 500: Internal Server Error.[/COLOR]**

:

---

### Post by kmitnick on 2009-05-26
first of all welcome
then nogomi website {  for arabic songs } "3rasi ya kbeer"
the link you are trying to download is a page that will redirect you to the mp3 file location so if you pass it to IE or FireFox it will redirect you to this
```
http://down3.nogomi.com.xn55571528exgem0o65xymsgtmjiy75924mjqqybp.nogomi.com/M12/Kazem_El_Saher/Ana_Wa_Laila/Nogomi.com_Kazem_El_Saher-Ana_Wa_Layla.mp3/[code]

so to download it to your Desktop press **Alt+F2** Then type **gnome-terminal** and run this
[code]cd Desktop
wget http://down3.nogomi.com.xn55571528exgem0o65xymsgtmjiy75924mjqqybp.nogomi.com/M12/Kazem_El_Saher/Ana_Wa_Laila/Nogomi.com_Kazem_El_Saher-Ana_Wa_Layla.mp3
```

---

### Post by m_adel on 2009-05-26
thnx  thnx 

"ya khayee" ;)

---

### Post by kmitnick on 2009-05-26
walao 3rasi, inta lebnani ???
anyway  if you need any help with ubuntu add me
[email]abedzaben_89@hotmail.com[/email]

---

