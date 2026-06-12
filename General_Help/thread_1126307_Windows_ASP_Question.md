---
title: "Windows ASP Question"
date: 2009-04-15
forum: General Help
---

### Post by CrusaderAD on 2009-04-15
I know, I know... it's a windows question. Well there's absolutely NO help in their forums. I'm trying to use the fax component from this site:

[http://support.microsoft.com/kb/303647]("http://support.microsoft.com/kb/303647")

But when I do, I get this error:

```
Server object error 'ASP 0178 : 80070005'

Server.CreateObject Access Error

/dhl/fax.asp, line 3

The call to Server.CreateObject failed while checking permissions. Access is denied to this object.
```

Here's te ASP page:

```
<%

Set FaxWrapper = Server.CreateObject("FaxComWrapper.FaxSend")

Dim strFileName
Dim strFaxMachine
Dim strFaxNumber

strFileName = "<Insert Filename Here>" 
strFaxMachine = "<Insert FaxMachine Here>" 
strFaxNumber = "<Insert FaxNumber Here>" 
 
FaxWrapper.SendFax strFileName, strFaxMachine, strFaxNumber

Set FaxWrapper = Nothing

%>
```

I searched all over for a solution but I still get the same error. I set permissions everywhere I can think of and everywhere I could find any recommendations. Any help please?

---

