---
title: "Help me to solve this problem"
date: 2007-12-03
forum: Education &amp; Science
---

### Post by sathish456 on 2007-12-03
i have a problem when i run the program in [http://localhost/xampp/htdocs/3.cgi](http://localhost/xampp/htdocs/3.cgi)

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>500 Internal Server Error</title>
</head><body>
<h1>Internal Server Error</h1>
<p>The server encountered an internal error or
misconfiguration and was unable to complete
your request.</p>
<p>Please contact the server administrator,
 [email]you@example.com[/email] and inform them of the time the error occurred,
and anything you might have done that may have
caused the error.</p>
<p>More information about this error may be available
in the server error log.</p>
<hr>
<address>Apache/2.2.2 (Unix) DAV/2 mod_ssl/2.2.2 OpenSSL/0.9.8b PHP/5.1.4 mod_apreq2-20051231/2.5.7 mod_perl/2.0.2 Perl/v5.8.7 Server at localhost Port 80</address>
</body></html>

---

### Post by meatpan on 2007-12-04
Here are some steps you can follow to start debugging your program:

o Like the server output message said, check the webserver logs.  Do this by running,   'sudo tail -f tail -f /var/log/apache2/error.log', in a terminal.   Once that command is running, re-execute the cgi script that is causing the problem.
o Post some more information.  The apache error message is too ambiguous to interpret without some understanding of your 3.cgi script.   Consider posting the error message from the bullet above, or the problem areas of 3.cgi.

---

