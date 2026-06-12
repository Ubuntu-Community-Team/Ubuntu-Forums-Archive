---
title: "Powerbuilder App on Wine accessing MySQL in UnixODBC"
date: 2006-08-16
forum: Desktop Environments
---

### Post by fhmanas on 2006-08-16
Hello, our organization is planning to move to a Linux environment, unfortunately, we do have Windows only apps that we need to port to the new environment.  We are testing in a test ubuntu dapper machine.

So far, we have managed to install the application on Ubuntu under WINE. The app was developed in PB5 and uses ODBC as access, the database is MySQL on a different machine. The app seems to have been installed properly as a popup window appears and the app is trying to connect to the database.  This is where the problem starts, the app does not seem to connect to the ODBC interface.  Configured the app in Winecfg to use the builtin ODBC32.dll which should hook up to UnixODBC, but I don't know if this is really happening.  I know UnixODBC is working since I can connect to the database using isql.  In addition, I checked the WINE environments like WINEDLLPATH and it is returning blank, should I set it manually or should it have been done automatically.

Thank you in advance for any help provided.

Francis

---

### Post by fhmanas on 2006-08-21
Just to update, got PB to work and connect via ODBC hooked up to unixODBC.  After some help from winehq live chat boards, was able to figure out that a libodbc.so was not linked properly, thus Wine ODBC (builtin) could not hook up with unixODBC.  Once that was correct by a simple symlink, everything was working already.

Am posting this to help others in similar situation.

---

### Post by fhmanas on 2008-04-24
For future reference, you can find instructions to hook up UnixODBC to WINE [here]("http://www.winehq.org/site/docs/wineusr-guide/misc-things-to-configure")

---

