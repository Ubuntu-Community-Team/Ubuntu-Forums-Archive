---
title: "Can't connect to MySQL database from OpenOffice"
date: 2007-07-18
forum: Desktop Environments
---

### Post by Zhanna on 2007-07-18
I'm using Ubuntu 7.04.  Trying to connect to an existing remote MySQL database through OpenOffice's database application.  My datasource URL and authentication information are correct (I have a WinXP machine that connects just fine), but I'm unable to connect from Ubuntu.  I get the following error:

SQL Status: S1000

Error during query: Unexpected Exception: java.io.CharConversionException message given: null

Nested Stack Trace:


** BEGIN NESTED EXCEPTION ** 

java.io.CharConversionException

STACKTRACE:

java.io.CharConversionException
   at gnu.gcj.convert.Input_iconv.read(libgcj.so.70)
   at java.lang.String.init(libgcj.so.70)
   at java.lang.String.<init>(libgcj.so.70)
   at com.mysql.jdbc.SingleByteCharsetConverter.<init>(SingleByteCharsetConverter.java:153)
   at com.mysql.jdbc.SingleByteCharsetConverter.initCharset(SingleByteCharsetConverter.java:108 )
   at com.mysql.jdbc.SingleByteCharsetConverter.getInstance(SingleByteCharsetConverter.java:86)
   at com.mysql.jdbc.StringUtils.getBytes(StringUtils.java:600)
   at com.mysql.jdbc.ByteArrayBuffer.writeStringNoNull(ByteArrayBuffer.java:544)
   at com.mysql.jdbc.MysqlIO.sqlQueryDirect(MysqlIO.java:1660)
   at com.mysql.jdbc.Connection.execSQL(Connection.java:3020)
   at com.mysql.jdbc.Connection.configureClientCharacterSet(Connection.java:2343)
   at com.mysql.jdbc.Connection.initializePropsFromServer(Connection.java:3748 )
   at com.mysql.jdbc.Connection.createNewIO(Connection.java:2585)
   at com.mysql.jdbc.Connection.<init>(Connection.java:1485)
   at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:266)


** END NESTED EXCEPTION **

:confused:  I can't find anything helpful online.  Does anyone have any ideas? 

Thanks!

Zhanna

---

### Post by JanvL on 2007-07-20
Not sure but:

Do you have jdbc installed?

Jan

---

### Post by Zhanna on 2007-07-20
Yes, I downloaded it from MySQL's site, and followed basically the instructions here (I can't find the exact site I used, but this is what I did):  [http://articles.techrepublic.com.com/5100-1035_11-6170388.html](http://articles.techrepublic.com.com/5100-1035_11-6170388.html)

So it seems to be installed properly and even seems to be communicating with the server, because when I type an incorrect username and/or password I get a message to that effect ... but with the correct username and password, I get the above bizarre error.  Maybe just a reinstall of JDBC is needed?  I don't know what else to try.

Zhanna

---

### Post by spikyjt on 2008-04-22
The mysql jdbc connector is in the repos. libmysql-java. I installed that and then added the class path /usr/share/java/mysql-connector-java.jar in openoffice options -> java. Re-start openoffice and it worked fine. Hope that works for you.

---

### Post by LiamTreacy on 2008-05-18
Any further help on this? OpenOffice doesn't connect to MySQL as far as I can see.

---

### Post by etunnels on 2008-06-05
I could never get the java connection to work either, but this article did a nice, quick job of helping me to connect using ODBC:

[http://www.linux.com/feature/60185](http://www.linux.com/feature/60185)

I followed this guide closely and had no problems connecting.

---

