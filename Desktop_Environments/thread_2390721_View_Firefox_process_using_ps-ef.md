---
title: "View Firefox process using ps-ef"
date: 2018-05-01
forum: Desktop Environments
---

### Post by cam17 on 2018-05-01
When I used ps-ef|grep firefox I received a strange result a shown below on my 16.04.4LTS desktop can anyone tell me what the numeric values are?

ps -ef|grep firefox
 mac       5427  1487  4 14:57 ?        00:00:37 /usr/lib/firefox/firefox
 mac       5478  5427  1 14:57 ?        00:00:07 /usr/lib/firefox/firefox -contentproc -childID 1 -isForBrowser -intPrefs 6:50|7:-1|19:0|34:1000|42:20|43:5|44:10|51:0|57:128|58:10000|63:0|65:400|66:1|67:0|68:0|69:100|74:0|75:120|76:120|159:2|160:1|164:60|165:30|166:512000|175:5000|177:6|191:8192|192:524288|193:5|206:10000|227:24|228:32768|230:1|231:2|240:5|244:1048576|246:100|247:5000|249:600|250:4|251:1|260:2000|277:3|290:60000|308:300|309:30| -boolPrefs 1:0|2:0|4:1|5:0|24:1|27:0|28:1|29:1|31:1|32:1|33:1|36:0|37:0|38:1|41:1|45:1|46:0|47:0|48:1|49:1|50:1|52:0|55:1|56:1|59:0|60:0|61:0|62:0|64:0|70:1|71:1|72:0|73:1|77:1|78:1|79:0|80:0|81:1|82:1|83:0|84:1|87:0|88:0|91:1|92:1|96:1|97:1|98:0|99:1|100:0|101:0|103:0|104:0|105:1|106:1|107:1|110:1|111:1|112:1|113:1|114:1|115:0|116:0|117:0|119:0|120:1|121:1|122:0|123:0|124:0|125:0|127:1|128:0|129:1|130:1|131:1|132:0|133:0|134:1|135:1|136:1|137:1|138:0|139:1|140:1|141:1|142:1|143:1|144:1|145:0|146:1|147:1|148:0|149:1|150:0|152:0|153:0|154:0|155:1|156:1|157:1|158:1|161:1|162:0|172:0|173:0|174:1|178:0|180:1|181:0|182:1|184:1|186:0|187:0|190:0|194:1|195:0|196:1|197:1|198:0|201:1|205:1|207:1|208:0|210:1|213:0|225:0|226:0|229:1|232:1|234:1|235:1|237:1|238:0|245:1|248:1|253:0|254:0|255:0|256:1|257:1|258:0|259:1|264:0|267:1|268:1|269:1|270:1|271:1|272:0|273:0|279:1|282:0|283:0|284:1|285:1|286:0|287:1|288:1|289:1|291:0|292:0|294:0|303:1|304:1|305:0|306:0|307:0| -stringPrefs 3:7;release|151:0;|212:3;1.0|223:332;  ¼½¾&#451;&#720;??&#1417;&#1418;[FONT=FreeSans]&#1475;&#1524;&#1545;&#1546;&#1642;&#1748;&#1793;&#1794;&#1795;&#1796;[/FONT][FONT=Noto Sans CJK SC Regular][SIZE=2]&#4447;&#5941;&#8192;&#8193;&#8194;&#8195;&#8196;&#8197;&#8198;&#8199;&#8200;&#8201;&#8202;[/SIZE][/FONT]???&#8208;’&#8228;&#8231;???????&#8239;‹›&#8257;&#8260;&#8274;&#8287;&#8531;&#8532;&#8533;&#8534;&#8535;&#8536;&#8537;&#8538;?&#8540;&#8541;&#8542;&#8543;&#8725;&#8758;&#9134;&#9585;&#10742;&#10744;&#11003;&#11005;[FONT=Noto Sans CJK SC Regular][SIZE=2]&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;[/SIZE][/FONT]&#42889;&#65044;&#65045;[FONT=Noto Sans CJK SC Regular][SIZE=2]&#65087;&#65117;&#65118;[/SIZE][/FONT]?[FONT=Noto Sans CJK SC Regular][SIZE=2]&#65294;&#65295;&#65377;&#65440;[/SIZE][/FONT]???&#65532;&#65533;|224:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 5427 true tab
 mac       5519  5427  0 14:57 ?        00:00:06 /usr/lib/firefox/firefox -contentproc -childID 2 -isForBrowser -intPrefs 6:50|7:-1|19:0|34:1000|42:20|43:5|44:10|51:0|57:128|58:10000|63:0|65:400|66:1|67:0|68:0|69:100|74:0|75:120|76:120|159:2|160:1|164:60|165:30|166:512000|175:5000|177:6|191:8192|192:524288|193:5|206:10000|227:24|228:32768|230:1|231:2|240:5|244:1048576|246:100|247:5000|249:600|250:4|251:1|260:2000|277:3|290:60000|308:300|309:30| -boolPrefs 1:0|2:0|4:1|5:0|24:1|27:0|28:1|29:1|31:1|32:1|33:1|36:0|37:0|38:1|41:1|45:1|46:0|47:0|48:1|49:1|50:1|52:0|55:1|56:1|59:0|60:0|61:0|62:0|64:0|70:1|71:1|72:0|73:1|77:1|78:1|79:0|80:0|81:1|82:1|83:0|84:1|87:0|88:0|91:1|92:1|96:1|97:1|98:0|99:1|100:0|101:0|103:0|104:0|105:1|106:1|107:1|110:1|111:1|112:1|113:1|114:1|115:0|116:0|117:0|119:0|120:1|121:1|122:0|123:0|124:0|125:0|127:1|128:0|129:1|130:1|131:1|132:0|133:0|134:1|135:1|136:1|137:1|138:0|139:1|140:1|141:1|142:1|143:1|144:1|145:0|146:1|147:1|148:0|149:1|150:0|152:0|153:0|154:0|155:1|156:1|157:1|158:1|161:1|162:0|172:0|173:0|174:1|178:0|180:1|181:0|182:1|184:1|186:0|187:0|190:0|194:1|195:0|196:1|197:1|198:0|201:1|205:1|207:1|208:0|210:1|213:0|225:0|226:0|229:1|232:1|234:1|235:1|237:1|238:0|245:1|248:1|253:0|254:0|255:0|256:1|257:1|258:0|259:1|264:0|267:1|268:1|269:1|270:1|271:1|272:0|273:0|279:1|282:0|283:0|284:1|285:1|286:0|287:1|288:1|289:1|291:0|292:0|294:0|303:1|304:1|305:0|306:0|307:0| -stringPrefs 3:7;release|151:0;|212:3;1.0|223:332;  ¼½¾&#451;&#720;??&#1417;&#1418;[FONT=FreeSans]&#1475;&#1524;&#1545;&#1546;&#1642;&#1748;&#1793;&#1794;&#1795;&#1796;[/FONT][FONT=Noto Sans CJK SC Regular][SIZE=2]&#4447;&#4448;&#5941;&#8192;&#8193;&#8194;&#8195;&#8196;&#8197;&#8198;&#8199;&#8200;&#8201;&#8202;[/SIZE][/FONT]???&#8208;’&#8228;&#8231;???????&#8239;‹›&#8257;&#8260;&#8274;&#8287;&#8531;&#8532;&#8533;&#8534;&#8535;&#8536;&#8537;&#8538;?&#8540;&#8541;&#8542;&#8543;&#8725;&#8758;&#9134;&#9585;&#10742;&#10744;&#11003;&#11005;[FONT=Noto Sans CJK SC Regular][SIZE=2]&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;[/SIZE][/FONT]&#42889;&#65044;&#65045;[FONT=Noto Sans CJK SC Regular][SIZE=2]&#65087;&#65117;&#65118;[/SIZE][/FONT]?[FONT=Noto Sans CJK SC Regular][SIZE=2]&#65294;&#65295;&#65377;&#65440;[/SIZE][/FONT]???&#65532;&#65533;|224:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 5427 true tab
 mac       5668  5427  1 15:07 ?        00:00:01 /usr/lib/firefox/firefox -contentproc -childID 3 -isForBrowser -intPrefs 6:50|7:-1|19:0|34:1000|42:20|43:5|44:10|51:0|57:128|58:10000|63:0|65:400|66:1|67:0|68:0|69:100|74:0|75:120|76:120|159:2|160:1|164:60|165:30|166:512000|175:5000|177:6|191:8192|192:524288|193:5|206:10000|227:24|228:32768|230:1|231:2|240:5|244:1048576|246:100|247:5000|249:600|250:4|251:1|260:2000|277:3|290:60000|308:300|309:30| -boolPrefs 1:0|2:0|4:1|5:0|24:1|27:0|28:1|29:1|31:1|32:1|33:1|36:0|37:0|38:1|41:1|45:1|46:0|47:0|48:1|49:1|50:1|52:0|55:1|56:1|59:0|60:0|61:0|62:0|64:0|70:1|71:1|72:0|73:1|77:1|78:1|79:0|80:0|81:1|82:1|83:0|84:1|87:0|88:0|91:1|92:1|96:1|97:1|98:0|99:1|100:0|101:0|103:0|104:0|105:1|106:1|107:1|110:1|111:1|112:1|113:1|114:1|115:0|116:0|117:0|119:0|120:1|121:1|122:0|123:0|124:0|125:0|127:1|128:0|129:1|130:1|131:1|132:0|133:0|134:1|135:1|136:1|137:1|138:0|139:1|140:1|141:1|142:1|143:1|144:1|145:0|146:1|147:1|148:0|149:1|150:0|152:0|153:0|154:0|155:1|156:1|157:1|158:1|161:1|162:0|172:0|173:0|174:1|178:0|180:1|181:0|182:1|184:1|186:0|187:0|190:0|194:1|195:0|196:1|197:1|198:0|201:1|205:1|207:1|208:0|210:1|213:0|225:0|226:0|229:1|232:1|234:1|235:1|237:1|238:0|245:1|248:1|253:0|254:0|255:0|256:1|257:1|258:0|259:1|264:0|267:1|268:1|269:1|270:1|271:1|272:0|273:0|279:1|282:0|283:0|284:1|285:1|286:0|287:1|288:1|289:1|291:0|292:0|294:0|303:1|304:1|305:0|306:0|307:0| -stringPrefs 3:7;release|151:0;|212:3;1.0|223:332;  ¼½¾&#451;&#720;??&#1417;&#1418;[FONT=FreeSans]&#1475;&#1524;&#1545;&#1546;&#1642;&#1748;&#1793;&#1794;&#1795;&#1796;[/FONT][FONT=Noto Sans CJK SC Regular][SIZE=2]&#4447;&#4448;&#5941;&#8192;&#8193;&#8194;&#8195;&#8196;&#8197;&#8198;&#8199;&#8200;&#8201;&#8202;[/SIZE][/FONT]???&#8208;’&#8228;&#8231;???????&#8239;‹›&#8257;&#8260;&#8274;&#8287;&#8531;&#8532;&#8533;&#8534;&#8535;&#8536;&#8537;&#8538;?&#8540;&#8541;&#8542;&#8543;&#8725;&#8758;&#9134;&#9585;&#10742;&#10744;&#11003;&#11005;[FONT=Noto Sans CJK SC Regular][SIZE=2]&#12272;&#12273;&#12274;&#12275;&#12276;&#12277;&#12278;&#12279;&#12280;&#12281;&#12282;&#12283;&#12288;&#12290;&#12308;&#12309;&#12339;&#12448;&#12644;&#12829;&#12830;&#13230;&#13231;&#13254;&#13279;[/SIZE][/FONT]&#42889;&#65044;&#65045;[FONT=Noto Sans CJK SC Regular][SIZE=2]&#65087;&#65117;&#65118;[/SIZE][/FONT]?[FONT=Noto Sans CJK SC Regular][SIZE=2]&#65294;&#65295;&#65377;&#65440;[/SIZE][/FONT]???&#65532;&#65533;|224:4;high| -schedulerPrefs 0001,2 -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 5427 true tab
 mac       5723  2447  0 15:09 pts/4    00:00:00 grep --color=auto firefox

---

### Post by TheFu on 2018-05-01
remove the **grep** and use **more** or** less** as the pager.  That will show the headers.  Then you can put the grep back.

---

### Post by cam17 on 2018-05-02
Why should I use anything other than Ps-ef? The output is incorrect and has no meaning. Is this a Ubuntu corruption?

---

### Post by TheFu on 2018-05-02
Sorry, my misunderstanding.  I thought you were looking for the headers from the ps command. My answer would tell you those.

But I think you are asking about firefox command line parameters instead.  [https://blog.mozilla.org/nnethercote/2018/02/22/nicer-commands-for-content-processes/](https://blog.mozilla.org/nnethercote/2018/02/22/nicer-commands-for-content-processes/) says FF v60 should clean up the startup parameters in the process table.  It hasn't been released.

More on FF startup options: [https://developer.mozilla.org/en-US/docs/Mozilla/Command_Line_Options](https://developer.mozilla.org/en-US/docs/Mozilla/Command_Line_Options)

This  has nothing to do with ps.  It is all Firefox.

---

### Post by kazakore on 2018-05-02
> **TheFu said:**
> https://blog.mozilla.org/nnethercote/2018/02/22/nicer-commands-for-content-processes/[/URL] says FF v60 should clean up the startup parameters in the process table.  It hasn't been released.



Saying even 18.04 only has FF59 in its repos where are you getting FF60 from???

---

### Post by TheFu on 2018-05-02
> **kazakore said:**
> Saying even 18.04 only has FF59 in its repos where are you getting FF60 from???
Read the link.

---

### Post by kazakore on 2018-05-02
> **TheFu said:**
> Read the link.

My apologies. I see it says it will be released in one week. Weird, as I went to install the British English language pack this morning (as I'm on a fresh install) and it came up with a message saying I needed to have FF60 to install it so I assumed it must be out already! Rather odd that they have addons only compatible with versions not even released yet!!

---

### Post by cam17 on 2018-05-02
Is this a bug? when I perform a ps-ef I can see all process clearly. Only when I look at Firefox specifically does it produce all that unreadable junk.

---

### Post by TheFu on 2018-05-02
My best guess explanation ... 

A terminal is an output device. Different terminals will handle odd characters differently.  Same for different filters like grep, more, less, anything that accepts either stdin or stderr as inputs.

I tested this on my desktop with firefox in an xterm - this is a terminal program from the 1990s.  less and more don't handle the odd output the same as grep.  When I used 'more', some output cause it to display the help for the program. The firefox odd characters also did this.  I don't think it is a bug, at least not in ps. Different terminals handle different characters differently too.

That's all I got.

---

