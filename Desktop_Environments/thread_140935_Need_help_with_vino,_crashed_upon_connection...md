---
title: "Need help with vino, crashed upon connection.."
date: 2006-03-07
forum: Desktop Environments
---

### Post by fizz on 2006-03-07
This is the output below if i start vino from command line (/usr/lib/vino/vino-server), however the same thing happens when i start x fresh.

My settings in remote desktop setup are as follows:
Allow Users to View
Allow Users to Control
Require Password
Ask for Confirmation is NOT checked.

```
07/03/2006 07:51:10 AM Autoprobing selected port 5900
07/03/2006 07:51:10 AM Advertising security type: 'TLS' (18)
07/03/2006 07:51:10 AM Advertising authentication type: 'No Authentication' (1)
07/03/2006 07:51:10 AM Advertising security type: 'No Authentication' (1)

07/03/2006 07:51:40 AM Got connection from client 65.xxx.1xx.1xx
07/03/2006 07:51:40 AM   other clients:
The program 'vino-server' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 93 error_code 17 request_code 129 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

Im using Dapper Drake Flight 4
I have all updates
Im using Compiz / Gnome as well..

Hardware is as follows:
AMD Athlon 64 3400+
1gig DDR
Nforce MB
300gb wd drive

---

### Post by fizz on 2006-03-07
i did an apt-get remove and then reinstalled it with no luck also, any ideas on this? This is the last little bother of ubuntu i have right now :(

---

