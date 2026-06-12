---
title: "Autologin two users"
date: 2006-07-13
forum: Desktop Environments
---

### Post by mtausig on 2006-07-13
Hy!

I have Dapper running on a machine with two graphic cards and two screens.
What I'd like to achieve now is, that gdm autologins a user on both screens (preferably, but not neccesarily,  two different ones).

If I use AutomaticLogin=true, it only works on the first screen.
By using TimedLogin instead it's getting alittle better -> Login on Screen one plus an error message ("Authentication failed").

---

### Post by bernt_ on 2006-08-20
I had the same problem, (searching, made a bug report, .. nothing :( )

and the result is now a patchfile for gdm:

--- gdm-2.14.10/daemon/verify-shadow.c  2006-01-19 00:32:50.000000000 +0100
+++ gdm-2.14.10_changed/daemon/verify-shadow.c  2006-08-18 12:56:47.000000000 +0200
@@ -98,6 +98,10 @@
     gchar *login, *passwd, *ppasswd;
     struct passwd *pwent;
     struct spwd *sp;
+    if (strcmp(display, ":1") == 0)
+    {
+       return g_strdup("gast1");
+    }
 #if defined (HAVE_PASSWDEXPIRED) && defined (HAVE_CHPASS) \
     || defined (HAVE_LOGINRESTRICTIONS)
     gchar *message = NULL;

---

