---
title: "Network printing broken"
date: 2008-08-28
forum: Desktop Environments
---

### Post by pssturges on 2008-08-28
Hi,

I have an HP deskjet 2100 printer connected to a mythbuntu 8.04.1 box. There are several other pc's connected to the local network, some winxp, some vista, and some ubuntu.

Printing had been set up and working well for about 6 months. I could print from the server and all the clients.

Recently, for no obvious reason I could see, network printing stopped working. I can still print from the server.

When I try to print from one of the ubuntu clients the print dialog comes up and the printer is visible, but the print button is greyed out and cannot be clicked.

Here is my cups config file:

```

# Show troubleshooting information in error_log.
LogLevel debug
SystemGroup lpadmin
# Allow remote access
Port 631
Listen /var/run/cups/cups.sock
# Show shared printers on the local network.
Browsing On
BrowseOrder allow,deny
BrowseAllow all
DefaultAuthType Basic
<Location />
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
<Policy default>
  <Limit Send-Document Send-URI Hold-Job Release-Job Restart-Job Purge-Jobs Set-Job-Attributes Create-Job-Subscription Renew-Subscription Cancel-Subscription Get-Notifications Reprocess-Job Cancel-Current-Job Suspend-Current-Job Resume-Job CUPS-Move-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Add-Modify-Printer CUPS-Delete-Printer CUPS-Add-Modify-Class CUPS-Delete-Class CUPS-Set-Default>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit Pause-Printer Resume-Printer Enable-Printer Disable-Printer Pause-Printer-After-Current-Job Hold-New-Jobs Release-Held-New-Jobs Deactivate-Printer Activate-Printer Restart-Printer Shutdown-Printer Startup-Printer Promote-Job Schedule-Job-After CUPS-Accept-Jobs CUPS-Reject-Jobs>
    AuthType Default
    Require user @SYSTEM
    Order deny,allow
  </Limit>
  <Limit CUPS-Authenticate-Job>
    Require user @OWNER @SYSTEM
    Order deny,allow
  </Limit>
  <Limit All>
    Order deny,allow
  </Limit>
</Policy>

```

Not sure what other configs/logs might be relevant, so please let me know and I'll post.

Thanks in advance for any help,

Phil

---

### Post by pssturges on 2008-08-29
Anyone, any ideas?

---

### Post by pssturges on 2008-10-29
I really need this fixed.

The printers appear on the clients, but when I try to print I get an error message saying the printer is not connected.

In the printer configuration dialog on the clients, all the settings for the printer are greyed out so they cannot be adjusted. If I then press the 'Goto server' button and enter the details for the server I get the following error: "There was an error during the CUPS operation 'httpConnectionEncrypt Failed'"

Any help much appreciated.

Phil

---

### Post by 080729jk on 2008-10-30
&#20844;&#21496;&#24120;&#24180;&#32463;&#33829;&#25104;&#37117;&#38050;&#38081;&#38598;&#22242;&#12289;&#20918;&#38050;&#38598;&#22242;&#12289;[&#26080;&#32541;&#38050;&#31649;](http://www.cnlcxb.com/wfgg.htm)&#21253;&#22836;&#38050;&#21378;&#12289;&#23453;&#38050;&#38598;&#22242;&#12289;&#23433;&#38050;&#38598;&#22242;&#12289;&#22825;&#27941;&#22823;&#26080;&#32541;&#12289;&#35199;&#23425;&#29305;&#38050;&#21378;&#12289;&#34913;&#38451;&#38050;&#21378;&#25152;&#29983;&#20135;&#30340;&#21508;&#31181;&#26080;&#32541;&#38050;&#31649;&#65292;&#27969;&#20307;&#31649;&#65292;&#39640;&#21387;&#38149;&#28809;&#31649;&#65292;&#21512;&#37329;&#31649;&#65292;&#39640;&#21387;&#31649;&#65292;&#21270;&#32933;&#19987;&#29992;&#31649;&#65292;&#22320;&#36136;&#31649;&#65292;&#34746;&#26059;&#31649;&#65292;&#30707;&#27833;&#35010;&#21270;&#31649;&#65292;&#25903;&#26550;&#31649;&#65292;&#27969;&#20307;&#31649;&#12290;&#20844;&#21496;&#26032;&#36817;&#21367;&#31649;&#26426;&#19968;&#22871;&#65292;&#21487;&#29983;&#20135;&#22806;&#24452;&#1060;377-1500mm&#22721;&#21402;10mm-60mm&#30340;&#39640;&#39057;&#28938;&#25509;&#38050;&#31649;&#65292;&#27426;&#36814;&#26032;&#32769;&#23458;&#25143;&#27965;&#35848;&#36873;&#36141;&#65281; &#12288;&#12288; &#29616;&#25105;&#20844;&#21496;&#26377;&#22823;&#37327;&#21512;&#37329;&#31649;&#12289;&#27969;&#20307;&#31649;&#65292;[&#26080;&#32541;&#38050;&#31649;](http://www.cnlcxb.com/wfgg.htm)&#39640;&#21387;&#38149;&#28809;&#31649;&#39640;&#21387;&#31649;&#29616;&#36135;&#65292;&#23558;&#20197;&#20248;&#24800;&#30340;&#20215;&#26684;&#65292;&#25209;&#38646;&#20860;&#33829;&#30340;&#26041;&#24335;&#65292;&#20026;&#24744;&#25552;&#20379;&#24555;&#25463;&#20248;&#36136;&#30340;&#26381;&#21153;&#65292;&#27426;&#36814;&#26032;&#32769;&#23458;&#25143;&#21069;&#26469;&#27965;&#35848;&#12289;&#30005;&#35758;&#12290; &#22791;&#27880;&#65306;&#65297;&#12289;&#20026;&#24744;&#22823;&#37327;&#20379;&#24212;&#21508;&#31181;&#29305;&#27530;&#22721;&#21402;&#65292;&#26448;&#36136;&#26080;&#32541;&#31649;&#65292;&#27969;&#20307;&#31649;&#65292;&#39640;&#21387;&#38149;&#28809;&#31649;&#65292;&#20919;&#25300;&#31934;&#23494;&#31649;&#21450;&#21508;&#31181;&#28909;&#25193;&#31649;&#12290;&#12288;&#12288;&#12288; &#65298;&#12289;&#25105;&#20204;&#30340;&#23447;&#26088;&#26159;&#65306;&#35753;&#24744;&#30465;&#38065;&#12289;&#30465;&#20107;&#12289;&#30465;&#24515;&#12290; &#12288;&#12288;&#20844;&#21496;&#21487;&#20026;&#29992;&#25143;&#35746;&#20570;&#21508;&#31181;&#29305;&#27530;&#35268;&#26684;&#65292;[&#26080;&#32541;&#38050;&#31649;](http://www.cnlcxb.com/wfgg.htm)&#29305;&#31181;&#26448;&#36136;&#38050;&#31649;&#65292;&#26080;&#32541;&#38050;&#31649;&#65292;&#27969;&#20307;&#31649;&#65292;&#39640;&#21387;&#38149;&#28809;&#31649;&#65292;&#20132;&#36135;&#21450;&#26102;&#65292;&#20215;&#26684;&#20302;&#65292;&#36136;&#37327;&#20248;&#65292;&#24182;&#38468;&#21407;&#22987;&#26448;&#36136;&#20070;&#25110;&#22797;&#21360;&#20214;&#65292;&#33410;&#20551;&#26085;&#29031;&#24120;&#33829;&#19994;&#12289;&#24182;&#21487;&#20195;&#21150;&#27773;&#36816;&#12289;&#28779;&#36816;&#65292;&#37327;&#22823;&#21487;&#20197;&#22312;&#38050;&#21378;&#30452;&#25509;&#21457;&#36135;&#12290;&#20134;&#21487;&#25215;&#20817;&#32467;&#31639;&#12290;&#12288;&#12288; &#22312;&#27492;&#65292;&#20844;&#21496;&#32463;&#29702;&#25658;&#20840;&#20307;&#21592;&#24037;&#65292;&#23558;&#20973;&#20511;&#33391;&#22909;&#30340;&#20449;&#35465;&#65292;&#38596;&#21402;&#30340;&#23454;&#21147;&#65292;&#20248;&#36136;&#30340;&#20135;&#21697;&#65292;&#20302;&#24265;&#30340;&#20215;&#26684;&#26381;&#21153;&#20110;&#24191;&#22823;&#29992;&#25143;.&#35880;&#21521;&#23545;&#20844;&#21496;&#19968;&#36143;&#32473;&#20104;&#20851;&#24576;&#12289;[&#38050;&#31649;](http://www.cnlcxb.com/)&#25903;&#25345;&#21644;&#24110;&#21161;&#30340;&#26032;&#32769;&#26379;&#21451;&#21644;&#24191;&#22823;&#23458;&#25143;&#34920;&#31034;&#34935;&#24515;&#30340;&#24863;&#35874;&#65281;&#24182;&#30495;&#35802;&#24076;&#26395;&#19982;&#20043;&#24314;&#31435;&#38271;&#26399;&#30340;&#21512;&#20316;&#20851;&#31995;&#65292;&#20114;&#24800;&#20114;&#21033;&#65292;&#20849;&#27714;&#21457;&#23637;&#12290;&#12288;&#12288; &#20184;&#27454;&#26041;&#24335;&#65306;&#20844;&#21496;&#20026;&#20102;&#30830;&#20445;&#36136;&#37327;&#38382;&#39064;&#65292;[&#38050;&#31649;](http://www.cnlcxb.com/)&#35753;&#26032;&#23458;&#25143;&#25918;&#24515;&#21487;&#36865;&#36135;&#21040;&#23478;&#65292;&#38050;&#31649;&#36135;&#21040;&#20184;&#27454;&#65281; &#12288;&#12288;&#32463;&#33829;&#29702;&#24565;&#65306;&#20197;&#36136;&#37327;&#27714;&#29983;&#23384;&#12289;&#20197;&#20449;&#35465;&#35851;&#21457;&#23637;&#12289;&#20197;&#30495;&#35802;&#20132;&#26379;&#21451;&#65281; &#12288;&#12288;&#20844;&#21496;&#23447;&#26088;&#65306;&#21331;&#36234;&#30340;&#20135;&#21697;&#65292;&#19968;&#27969;&#30340;&#26381;&#21153;&#65292;&#20197;&#35802;&#20449;&#20026;&#26412;&#65292;&#20197;&#20449;&#35465;&#27714;&#21457;&#23637;&#12290; &#12288;&#12288;&#32463;&#33829;&#23447;&#26088;&#65306;&#35802;&#20449;&#12289;&#21153;&#23454;&#12289;&#39640;&#25928;&#12290;&#12288;&#12288;&#27426;&#36814;&#21508;&#30028;&#26379;&#21451;&#33669;&#20020;&#25105;&#20844;&#21496;&#21496;&#23454;&#22320;&#21442;&#35266;&#32771;&#26597;&#12290;&#25105;&#20204;&#23558;&#20197;&#8220;&#20248;&#33391;&#30340;&#21697;&#36136;&#12289;&#20248;&#24800;&#30340;&#20215;&#26684;&#12289;&#20248;&#36136;&#30340;&#26381;&#21153;&#8221;&#22238;&#25253;&#32473;&#27599;&#19968;&#20301;&#39038;&#23458;&#12290;

---

### Post by rufia on 2009-06-04
I had the same problem when I installed Ubunbtu 8.10 on a pc with a backup I made with remastersys.  If i tried to stop and start or restart cups it gave me the following message:

*cupsd: Child exited with status 1!*

To fix the problem I typed the following command in terminal:

***sudo apt-get install --reinstall ssl-cert***

It gives you a verification message, so it is up to you whether you accept or not.

Restart your PC afterwards.  Hope it works for everyone.

---

### Post by rpi+ on 2009-08-15
To rufia!

Your posting solved my problem. Thanks a lot!

(My Problem and the solution:

II made a DVD on machine 1 with Ubuntu 9.04 and a locally by USB connected printer with 
   [FONT=Courier New]$ remastersys backup
[FONT=Verdana]then installed the DVD on machine 2 and did not even see the printer on machine 1 in the local network. I too got this message:
[/FONT][/FONT][FONT=Courier New]cupsd: Child exited with status 1![/FONT]

After your suggestion
   ***sudo apt-get install --reinstall ssl-cert***
accepting and reboot

everything worked fine!)


rpi.

---

