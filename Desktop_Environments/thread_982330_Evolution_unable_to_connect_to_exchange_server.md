---
title: "Evolution unable to connect to exchange server"
date: 2008-11-14
forum: Desktop Environments
---

### Post by DrSkalpell on 2008-11-14
Hi,

I have tried to set up evolution with Microsoft Exchange, but I get the following error message when I try to authenticate my settings:
"Could not authenticate to server"

- Username like "domain\uname"
- OWA URL like "https://mail.mail-server.com" or "https://mail.mail-server.com/exchange"

I started evolution with "E2K_DEBUG=5 evolution", and got the following log when I tried to authenticate:
```

->url' failed
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Exchange'
> GET / HTTP/1.1
> Soup-Debug-Timestamp: 1226696313
> Soup-Debug: SoupSessionSync 1 (0xa4f4368), SoupMessage 1 (0xa6879b8), SoupSocket 1 (0xa846150)
> Host: mail.mail-server.com
> Accept-Language: en-US, en
> Authorization: NTLM TlRMTVNTUAABAAAABoIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMAAAAAAAAAAwAAAA
> User-Agent: Evolution/2.24.1
  
< HTTP/1.1 302 Moved Temporarily
< Soup-Debug-Timestamp: 1226696313
< Soup-Debug: SoupMessage 1 (0xa6879b8)
< Location: https://mail.mail-server.com/CookieAuth.dll?GetLogonWrapper?url=%2F&reason=0
< Set-Cookie: sessionid=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
< Set-Cookie: cadata=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
< Connection: close
< Content-Length: 0
  
> GET / HTTP/1.1
> Soup-Debug-Timestamp: 1226696313
> Soup-Debug: SoupSessionSync 1 (0xa4f4368), SoupMessage 2 (0xa687a68), SoupSocket 2 (0xa511390)
> Host: mail.mail-server.com
> Authorization: NTLM TlRMTVNTUAABAAAABoIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMAAAAAAAAAAwAAAA
> User-Agent: Evolution/2.24.1
  
< HTTP/1.1 302 Moved Temporarily
< Soup-Debug-Timestamp: 1226696313
< Soup-Debug: SoupMessage 2 (0xa687a68)
< Location: https://mail.mail-server.com/CookieAuth.dll?GetLogonWrapper?url=%2F&reason=0
< Set-Cookie: sessionid=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
< Set-Cookie: cadata=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
< Connection: close
< Content-Length: 0
  
> GET /CookieAuth.dll?GetLogonWrapper?url=%2F&reason=0 HTTP/1.1
> Soup-Debug-Timestamp: 1226696313
> Soup-Debug: SoupSessionSync 1 (0xa4f4368), SoupMessage 2 (0xa687a68), SoupSocket 3 (0xa846108), restarted
> Host: mail.mail-server.com
> User-Agent: Evolution/2.24.1
> Authorization: NTLM TlRMTVNTUAABAAAABoIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMAAAAAAAAAAwAAAA
  
< HTTP/1.1 200 OK
< Soup-Debug-Timestamp: 1226696313
< Soup-Debug: SoupMessage 2 (0xa687a68)
< Pragma: no-cache
< Cache-control: no-cache,max-age=0,must-revalidate
< Content-Length: 989
< Connection: close
< 
< <!--Copyright (c) 2000-2003 Microsoft Corporation. All rights reserved.-->
< <HTML>
< <HEAD>
< <META HTTP-EQUIV="Content-Type" CONTENT="text/html; CHARSET=UTF-8">
< <TITLE>Microsoft Outlook Web Access</TITLE>
< </HEAD>
< <script language="JavaScript">
< function WarnOnLogoff()
< {
<    try
<    {
<        if (document.cookie != null && document.cookie != "" && document.cookie.indexOf("sessionid=") != -1 && document.cookie.indexOf("sessionid=;") == -1)
<        {
<           window.open("https://mail.mail-server.com/exchange/?Cmd=logoff");
<        }
<    }
<    catch(e)
<    {
<        window.open("https://mail.mail-server.com/exchange/?Cmd=logoff");    
<    }
< }
< </script>
< <FRAMESET onunload="WarnOnLogoff()" cols="100%, *" rows="100%,*" border="1" frameborder="1" framespacing="0" topmargin="0" leftmargin="0">
<     <FRAME name="owa" src="/CookieAuth.dll?GetLogon?url=%2F&amp;reason=0" frameborder="0" marginheight="0" marginwidth="0" scrolling="auto" border="1">
< </FRAMESET>
< </HTML>
< 
< 
< 
  
> GET /exchange/ HTTP/1.1
> Soup-Debug-Timestamp: 1226696313
> Soup-Debug: SoupSessionSync 1 (0xa4f4530), SoupMessage 1 (0xa687b70), SoupSocket 1 (0xa846438)
> Host: mail.mail-server.com
> Accept-Language: en-US, en
> Authorization: NTLM TlRMTVNTUAABAAAABoIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMAAAAAAAAAAwAAAA
> User-Agent: Evolution/2.24.1
  
< HTTP/1.1 302 Moved Temporarily
< Soup-Debug-Timestamp: 1226696313
< Soup-Debug: SoupMessage 1 (0xa687b70)
< Location: https://mail.mail-server.com/CookieAuth.dll?GetLogonWrapper?url=%2Fexchange%2F&reason=0
< Set-Cookie: sessionid=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
< Set-Cookie: cadata=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
< Connection: close
< Content-Length: 0
  
> GET /exchange/ HTTP/1.1
> Soup-Debug-Timestamp: 1226696313
> Soup-Debug: SoupSessionSync 1 (0xa4f4530), SoupMessage 2 (0xa69dc60), SoupSocket 2 (0xa846438)
> Host: mail.mail-server.com
> Authorization: NTLM TlRMTVNTUAABAAAABoIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMAAAAAAAAAAwAAAA
> User-Agent: Evolution/2.24.1
  
< HTTP/1.1 302 Moved Temporarily
< Soup-Debug-Timestamp: 1226696313
< Soup-Debug: SoupMessage 2 (0xa69dc60)
< Location: https://mail.mail-server.com/CookieAuth.dll?GetLogonWrapper?url=%2Fexchange%2F&reason=0
< Set-Cookie: sessionid=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
< Set-Cookie: cadata=; path=/; expires=Thu, 01-Jan-1970 00:00:00 GMT
< Connection: close
< Content-Length: 0
  
> GET /CookieAuth.dll?GetLogonWrapper?url=%2Fexchange%2F&reason=0 HTTP/1.1
> Soup-Debug-Timestamp: 1226696313
> Soup-Debug: SoupSessionSync 1 (0xa4f4530), SoupMessage 2 (0xa69dc60), SoupSocket 3 (0xa846108), restarted
> Host: mail.mail-server.com
> User-Agent: Evolution/2.24.1
> Authorization: NTLM TlRMTVNTUAABAAAABoIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAMAAAAAAAAAAwAAAA
  
< HTTP/1.1 200 OK
< Soup-Debug-Timestamp: 1226696314
< Soup-Debug: SoupMessage 2 (0xa69dc60)
< Pragma: no-cache
< Cache-control: no-cache,max-age=0,must-revalidate
< Content-Length: 1000
< Connection: close
< 
< <!--Copyright (c) 2000-2003 Microsoft Corporation. All rights reserved.-->
< <HTML>
< <HEAD>
< <META HTTP-EQUIV="Content-Type" CONTENT="text/html; CHARSET=UTF-8">
< <TITLE>Microsoft Outlook Web Access</TITLE>
< </HEAD>
< <script language="JavaScript">
< function WarnOnLogoff()
< {
<    try
<    {
<        if (document.cookie != null && document.cookie != "" && document.cookie.indexOf("sessionid=") != -1 && document.cookie.indexOf("sessionid=;") == -1)
<        {
<           window.open("https://mail.mail-server.com/exchange/?Cmd=logoff");
<        }
<    }
<    catch(e)
<    {
<        window.open("https://mail.mail-server.com/exchange/?Cmd=logoff");    
<    }
< }
< </script>
< <FRAMESET onunload="WarnOnLogoff()" cols="100%, *" rows="100%,*" border="1" frameborder="1" framespacing="0" topmargin="0" leftmargin="0">
<     <FRAME name="owa" src="/CookieAuth.dll?GetLogon?url=%2Fexchange%2F&amp;reason=0" frameborder="0" marginheight="0" marginwidth="0" scrolling="auto" border="1">
< </FRAMESET>
< </HTML>


```

Any ideas?

---

