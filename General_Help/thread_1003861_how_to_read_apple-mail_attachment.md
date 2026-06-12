---
title: "how to read apple-mail attachment"
date: 2008-12-06
forum: General Help
---

### Post by UphillSkier on 2008-12-06
Hi folks

Someone  has sent me a report in a file called "noname" attached to an email I received via gmail.  I downloaded it and discovered it was a text file 
```

mullera@happy:~/Desktop$ file noname 
noname: ASCII text

```

but the contents are clearly a .doc file  encoded as text. The first few lines are
```

mullera@happy:~/Desktop$ more noname 

--Apple-Mail-10-1004339614
Content-Transfer-Encoding: base64
Content-Type: application/applefile;
	name=YSHYMdelegatereport.doc
Content-Disposition: attachment;
	filename=YSHYMdelegatereport.doc

AAUWBwACAAAAAAAAAAAAAAAAAAAAAAAAAAMAAAAJAAAAPgAAAAoAAAADAAAASAAAABcAAAACAAAA
XwAAAR5XOEJOTVNXRAAAWVNIWU1kZWxlZ2F0ZXJlcG9ydC5kb2MAAAEAAAABAAAAAAAAAAAeAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
AAAAAAAAAAAAAAABAAAAAQAAAAAAAAAAHgAAAAAAAAAAABwAHv//

--Apple-Mail-10-1004339614
Content-Transfer-Encoding: base64
Content-Type: application/octet-stream;
	x-mac-type=5738424E;
	x-unix-mode=0644;
	x-mac-creator=4D535744;
	name=YSHYMdelegatereport.doc
Content-Disposition: attachment;
	filename=YSHYMdelegatereport.doc

0M8R4KGxGuEAAAAAAAAAAAAAAAAAAAAAPgADAP7/CQAGAAAAAAAAAAAAAAABAAAAJQAAAAAAAAAA
EAAAJwAAAAEAAAD+////AAAAACQAAAD/////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////////
////////////////////////////////////////////////////////////////////////////

```

Can someone point me to a tool for decoding this?

Thanks

Andrew Muller

---

### Post by UphillSkier on 2008-12-06
Ok, I found the tool by using synaptic to browse the package library and searching for "base64".  "uudeview " works just fine.
```

mullera@happy:~/Desktop$ uudeview noname 
Loaded from noname: '' (YSHYMdelegatereport.doc): YSHYMdelegatereport.doc part 1   Base64
Loaded from noname: '' (YSHYMdelegatereport.doc): YSHYMdelegatereport.doc part 1   Base64
                                                                      
Found 'YSHYMdelegatereport.doc' State 16 Base64 Parts 1 OK
Found 'YSHYMdelegatereport.doc' State 16 Base64 Parts 1 OK            

  -rw-r--r-- YSHYMdelegatereport.doc is OK   [d] (?=help) ?

<snip>

  -rw-r--r-- YSHYMdelegatereport.doc is OK   [d] (?=help) d
Opened file noname
    File successfully written to /home/mullera/Desktop/YSHYMdelegatereport.doc
  -rw-r--r-- YSHYMdelegatereport.doc is OK   [d] (?=help) r
Enter new filename: YSHYMdelegatereport-2.doc
  -rw-r--r-- YSHYMdelegatereport-2.doc is OK   [d] (?=help) d
Opened file noname
    File successfully written to /home/mullera/Desktop/YSHYMdelegatereport-2.doc
2 files decoded from 1 input file, 0 failed   
```

---

