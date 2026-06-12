---
title: "WGET with Redirects"
date: 2005-12-29
forum: General Help
---

### Post by sciurus on 2005-12-29
I'm trying to download the file TBP-Base-3_2.exe from [http://www.filedomain.stargame.co.uk/download.php?file=3](http://www.filedomain.stargame.co.uk/download.php?file=3). Whenever I click the link in Firefox it starts to save correctly. However, if I try to do it with wget it only downloads a php file. Does anyone have an idea why the redirect works differently in wget than in firefox and how to fix it?

```
wget -S  http://www.filedomain.stargame.co.uk/download.php?file=3
--15:17:07--  http://www.filedomain.stargame.co.uk/download.php?file=3
           => `download.php?file=3'
Resolving www.filedomain.stargame.co.uk... 64.151.213.11
Connecting to www.filedomain.stargame.co.uk|64.151.213.11|:80... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 302
  Date: Thu, 29 Dec 2005 20:21:47 GMT
  Server: Apache/2.0.51 (Fedora)
  X-Powered-By: PHP/4.3.10
  Expires: Thu, 19 Nov 1981 08:52:00 GMT
  Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
  Pragma: no-cache
  Set-Cookie: PHPSESSID=4dbd991cc7a07abd9be8c250fec786a5; path=/
  Location: download.php?go=2&file=3&mirror=3
  Connection: close
  Content-Type: text/html
**Location: download.php?go=2&file=3&mirror=3 (following)**
--15:17:08--  http://www.filedomain.stargame.co.uk/download.php?go=2&file=3&mirror=3
           => `download.php?go=2&file=3&mirror=3'
Connecting to www.filedomain.stargame.co.uk|64.151.213.11|:80... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 302
  Date: Thu, 29 Dec 2005 20:21:47 GMT
  Server: Apache/2.0.51 (Fedora)
  X-Powered-By: PHP/4.3.10
  Expires: Thu, 19 Nov 1981 08:52:00 GMT
  Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
  Pragma: no-cache
  Location: details.php?file=3
  Connection: close
  Content-Type: text/html
**Location: details.php?file=3 (following)**
--15:17:08--  http://www.filedomain.stargame.co.uk/details.php?file=3
           => `details.php?file=3'
Connecting to www.filedomain.stargame.co.uk|64.151.213.11|:80... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 200 OK
  Date: Thu, 29 Dec 2005 20:21:48 GMT
  Server: Apache/2.0.51 (Fedora)
  X-Powered-By: PHP/4.3.10
  Expires: Thu, 19 Nov 1981 08:52:00 GMT
  Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
  Pragma: no-cache
  Connection: close
  Content-Type: text/html
Length: unspecified (text/html)

    ( <=>                                 ) 9,658         49.20K/s             

15:17:09 (49.15 KB/s) - `details.php?file=3' saved (9658)

```

---

### Post by Zalbor on 2005-12-29
wget simply downloads the file you tell it to. Firefox understands php so it gets redirected.
As for how to solve it, not sure. Maybe you could open the php file and try to see where it redirects to?

---

### Post by sciurus on 2005-12-29
I installed the livhttpheaders extensionfor firefox.

```

http://www.filedomain.stargame.co.uk/download.php?file=3



GET /download.php?file=3 HTTP/1.1

Host: www.filedomain.stargame.co.uk

User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)

Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

Accept-Language: en-us,en;q=0.5

Accept-Encoding: gzip,deflate

Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7

Keep-Alive: 300

Connection: keep-alive

Referer: http://www.filedomain.stargame.co.uk/files.php?cat=6

Cookie: PHPSESSID=485778710d4cdbd3e75a46d267eae166



HTTP/1.x 302 OK

Date: Fri, 30 Dec 2005 03:28:36 GMT

Server: Apache/2.0.51 (Fedora)

X-Powered-By: PHP/4.3.10

Expires: Thu, 19 Nov 1981 08:52:00 GMT

Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0

Pragma: no-cache

**Location: download.php?go=2&file=3&mirror=3**

Keep-Alive: timeout=15, max=94

Connection: Keep-Alive

Transfer-Encoding: chunked

Content-Type: text/html

----------------------------------------------------------

http://www.filedomain.stargame.co.uk/download.php?go=2&file=3&mirror=3



GET /download.php?go=2&file=3&mirror=3 HTTP/1.1

Host: www.filedomain.stargame.co.uk

User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)

Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

Accept-Language: en-us,en;q=0.5

Accept-Encoding: gzip,deflate

Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7

Keep-Alive: 300

Connection: keep-alive

Referer: http://www.filedomain.stargame.co.uk/files.php?cat=6

Cookie: PHPSESSID=485778710d4cdbd3e75a46d267eae166



HTTP/1.x 302 OK

Date: Fri, 30 Dec 2005 03:28:36 GMT

Server: Apache/2.0.51 (Fedora)

X-Powered-By: PHP/4.3.10

Expires: Thu, 19 Nov 1981 08:52:00 GMT

Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0

Pragma: no-cache

**Location: http://www.filedomain.net/downloads/tbp/TBP-Base-3_2.exe**

Keep-Alive: timeout=15, max=100

Connection: Keep-Alive

Transfer-Encoding: chunked

Content-Type: text/html

----------------------------------------------------------

http://www.filedomain.net/downloads/tbp/TBP-Base-3_2.exe



GET /downloads/tbp/TBP-Base-3_2.exe HTTP/1.1

Host: www.filedomain.net

User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.12) Gecko/20051010 Firefox/1.0.7 (Ubuntu package 1.0.7)

Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5

Accept-Language: en-us,en;q=0.5

Accept-Encoding: gzip,deflate

Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7

Keep-Alive: 300

Connection: keep-alive

Referer: http://www.filedomain.stargame.co.uk/files.php?cat=6



HTTP/1.x 200 OK

Date: Fri, 30 Dec 2005 03:23:57 GMT

Server: Apache/1.3.33

Last-Modified: Wed, 21 Sep 2005 19:16:19 GMT

Etag: "24d2bd-105c1951-4331b183"

Content-Length: 274471249

Keep-Alive: timeout=5, max=100

Connection: Keep-Alive

Content-Type: application/octet-stream


```

I guess the site gives out different redirects based on the cookie.

---

### Post by Kevinator on 2005-12-30
I believe wget can handle cookies. I can also change its user agent string. If you use the right options the server shouldn't know the difference between Firefox and wget.

---

