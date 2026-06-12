---
title: "qtstalker yahoo plugin"
date: 2007-03-11
forum: Desktop Environments
---

### Post by jacksonz123z on 2007-03-11
I think Yahoo have changed their date format, so that now the Yahoo plugin for Qtstalker will not download historical data.  The quote mode still works.
Has anyone solved this problem?  I tried to recompile from the CVS but did not succeed.  Could someone give some advice on compiling Qtstalker.  I think my  problem lay with qt development dependencies?  The Qtstalker version in Feisty is still broken!
I find this very useful software.

---

### Post by wgrant on 2007-03-17
Yahoo changed the date format in their data. I've added a fix to the Feisty version, and will look at getting the fix into Dapper and Edgy. Thanks a lot, Yahoo!

---

### Post by jacksonz123z on 2007-03-17
I really appreciate your help and rapid response.  Qtstalker is very useful!  Thanks again.:)

---

### Post by wron_00 on 2007-07-07
How do I enter symbols or get it to retrieve all of Yahoo's last quotes?  Does it only work while the market is open?  
I have gone to Download the Quotes from the Internet  --> Chose under Plug-ins Yahoo --> then selected Update (above) --> I get "no symbols selected" -->  how do I select symbols and such forth?  does this app work where it will search through various specifications and pull up those stocks?  Or does it only pull up the stocks you specifically enter the symbols for?

Linux/Ubuntu 7.04 newbie,

J. Wright

---

### Post by jacksonz123z on 2007-07-07
Yes first select the Yahoo plugin, then go to Yahoo Prefs by clicking the "spanner icon".  In this screen you select the stocks by clicking the button beneath the Yahoo tab. Enter the symbols separated by a space.  I had to enter the country specific code, eg  BPT.AX.  AX is the country code for Australia.  You can determine the country code by going to Yahoo.
The APP works out of market time.  Apparently you can scan against various parameters, but I have not done this, I think scripting might be required.  Hope this helps.

---

### Post by Old Beach Dog on 2007-08-08
I have just installed QtStalker (Vers 0.26)  from Dapper.  The Yahoo "quote" works but there is no "history" download for US or Australian stocks.  Should I move to a higher level version, try Feisty or something else.

---

### Post by Hampster on 2007-08-08
I would very much like to use qtstalker but have struck the problem of bad dates from yahoo.  Just keeping the thread alive in hope that someone can sort the problem for edgy users (and others?).  Sorry if I have overstepped any marks but .....  I gotta get back in the market.  Any suggestions?  Also is there a dedicated users group for qtstalker??  

My first post.....  I love ubuntu.... honest I do,I do I do I do I do I do. :guitar:

---

### Post by wgrant on 2007-08-08
> **Old Beach Dog said:**
> I have just installed QtStalker (Vers 0.26)  from Dapper.  The Yahoo "quote" works but there is no "history" download for US or Australian stocks.  Should I move to a higher level version, try Feisty or something else.

Feisty will definitely work; I fixed and used it myself.

---

### Post by Old Beach Dog on 2007-08-08
Many thanks.  I have installed Qtstalker 0.32 and it is working great.  Working my way through the manual/instructions.  I have been a Omega Supercharts user for 12 years so am a little set in my thinking, but Qtstalker looks very good.  Being new to Linux, etc I am still easily confused. However I am making steady progress and enjoying kissing "Uncle Bill" goodbye.

---

### Post by dedlycow on 2007-08-09
I too have just downloaded qt stalker about 2 weeks ago Im both new to Ubuntu and  the stock market so its all abit daunting but am looking foward to learning. I finnaly got my first stock down loaded tonight and i am very happy.
Ps has anyone had any luck running Commsec pro trader on linux? 
Dedlycow

---

### Post by Hampster on 2007-08-10
Good luck guys with the program.  

Heh Fujittsu
Is there any chance that it can be made to work with Edgy or do I have to risk upgrading to Fawn?  I am very new to Ubuntu and it hasn't been easy--- Actually it's been a bit of a minefield so consequently I am reluctant to change just yet now that I have got things relatively where I can use my comp again.

I would ever so much appreciate .....etc etc.. please please please Thankyou thankyou ....:)

---

### Post by Old Beach Dog on 2007-08-13
Qtstalker 0.32 is working well (5 days experience).  Can someone advise me  how to enter an index code.  I have tried ^AXJO.AX ( for ASX S&P 200 index) and download appears to complete normally.  However no data is available to chart or shows in the data window. Volatility is good!

---

### Post by Hampster on 2007-08-14
Sounds like you are happy OBD. Good on you.  I am still hamstrung with the bad dates thingy from Yahoo.  I have PM'ed Fujitsu but have to assume that he has a real job and might even have this terrible lurgi and be in bed.  Oh well ....patience.  sorry I can't help with your problem.  Good luck with your stock research.  Meanwhile.. any clues on a user group?

---

### Post by nearly_nickless_head on 2007-08-17
how can i make qtstalker work behind a proxy?
i am new to stocks....but i would like to learn fast.
Thanks in advance......:)

---

### Post by wgrant on 2007-08-18
I'm a little busy at the moment with real work and my final year of school coming to an end in the next couple of months. We really don't have the manpower to support universe in a whole lot of previous releases, so basically only Dapper and Feisty are receiving non-critical fixes at this time. Based on that, upgrading to Feisty would be your best bet, as I can't see me having time to convince people it's a good idea to backport the fix to Edgy.

---

### Post by Old Beach Dog on 2007-08-18
Fujitsu - Best of luck with your studies from all of us.  :KS   I have found Ubuntu 7.04 very stable and easy to use, etc.

My last query on market indice stock has been solved by trial (and a few "no results").   A market indice can be downloaded by going to the Yahoo data site and finding the code (eg ^AXJO - for Australian Exchange top 200 stocks) and downloading without the exchange extension .AX.  This means it is stored in the US Stocks folder, but a group can be set with Aussie Indices for easier access.

Can anyone advise if an Market Stock or Indice chart  or index (plug in ) chart can be displayed in the "tabbed" or other area while a standard stock is is displayed in the main area?    This is a key part of Stan Weinstein's market tracking ( from his book  " Secrets For Profiting in Bull and Bear Markets" which is the only stock book I  have now.  I have given the rest away).

---

### Post by Hampster on 2007-08-19
Big smiles......   Thanks for your efforts Fujitsu and good luck with exams.  I had already come to the conclusion that I should just bite the bullet and upgrade to feisty.  Qtstalker appears to be working just fine.  Thanks again.  

I am new to learning to drive the prog. so can't help O/B/Dog sorry...

---

### Post by Hampster on 2007-08-21
I have just realized that this may not be the right forum for QTstalker problems.  If I am right can anyone point me in the right direction....   I have two concerns.  

1. I don't have a help file and haven't had one since the initial downloading.  Is there a help file and if so where do I find it and can it be downloaded.. 

 2.  Just how often does Yahoo update the info.  It is now 3.45 pm on Tuesday and there are no results for yesterdays trading yet???

---

### Post by Old Beach Dog on 2007-08-29
Hello Hampster  -  on your queries -

1.  I have done some searches and cannot find another forum for Qtstalker issues.  You could try [http://sourceforge.net/forum/forum.php?forum_id=80701](http://sourceforge.net/forum/forum.php?forum_id=80701) - which may be of some help.

2.  When I downloaded Qtstalker 0.32 (and pre reqs) I also downloaded Qtstalker-doc 0.32, which installed OK and was available in Qtstalker without any further actions.

3.  The updating times of Yahoo is not specified anywhere, even on their site [http://finance.yahoo.com/](http://finance.yahoo.com/).   At 5.40pm WED the data for TUES is not available for  download. 
Further update on this item.
At 0835 AEST on THURS I used "Quote" in place of "Auto History" to download WED data.  The O/H/L/C data appears to be the close of WED trading although Volume is not correct (possibly the last ten minutes). The price data is probably available earlier.  On FRI at 1700 I downloaded WED  data using "Auto History" and the prices remained the same and the Vol appears to be correct for the day.   Need more trials to find earliest time price data available.   AT 1730 FRI I ran "Quote" and received  O/H/L/C for FRI, but no THURS data.  Your update may need to be in Steps - say "Quote" 1 hour after close of trading and later for "Auto History".  Need more playtime.  Can't help for 5 weeks as I am O/S. 
Sorry to be of limited help.

---

### Post by Hampster on 2007-08-31
Hi OBD,  Thanks for your reply.  We can only but keep on keeping on and see what happens.  Good luck and safe travels..

---

### Post by jacksonz123z on 2007-09-12
Looks like Yahoo have changed their date format again or even their address, because Qtstalker has stopped downloading data as of the 7/9/07.  Any help would be appreciated.

---

### Post by dedlycow on 2007-09-18
Hello Qt stalker users
I am having trouble with QT3.2 not downloading data. Sometimes its days late. For example today is 18/9 and the latest data I can get is 10 /9, also I too have no 'help info' with my copy. I'm using Feisty. any help would be good. I'm Dedly cow on Skype If any body is able to help.
thanks Dedly

---

### Post by jacksonz123z on 2007-09-18
Looks like Yahoo have changed the data web address.  I think the only way to fix this is download from CVS and compile the latest version.  I will have a go at this soon.  Previous attempts have not gone well.  Any help would be appreciated.

---

### Post by jacksonz123z on 2007-10-06
Debs from Marco's repository [http://www.zwets.com/debs]("http://www.zwets.com/debs") used in Gutsy will fix the Yahoo quote problem and give the latest Qtstalker.  Because of dependency problems these packages will not work in Feisty.

---

