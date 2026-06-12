---
title: "gdesklets news rss feed"
date: 2005-12-17
forum: Desktop Environments
---

### Post by michael_salcher on 2005-12-17
Has anyone got gdesklets with News RSS Grabber v1.5 using the Google News RSS feed working?
First of all, the gdesklet does not display any Google News at all and second when I try a different RSS feed (e.g. slashdot) I get an error when clicking the little "down" arrow to display news:

NoneType' object is not callable                                                    
/home/mike/.gdesklets/Displays/NewsGrab/newsgrab.script                              
  589                                   Dsp.time[i].value = item[i + pos][3]         
  590                                                                                
  591           refresh_arrows()                                                     
  592                                                                                
  593           if news.refresh == 1:                                                
> 594                   news.refresh = 0                                             

  595                   if wrap != width:                                            
  596                           set_wrap(width)                                      
  597                                                                                
  598                   update_actions()                                             
  599                   refresh_newsitems()                                          
  600                                     

Any ideas?

---

### Post by Julio Viana on 2008-02-11
Maybe is late for you but no for other people with this problem ;)

You need to install it manually.

1) Run the next program in graphical mode (This creates the config directory in your user folder)
# gdesklets shell

2) Now in a console window go to your user home directory (/home/YouUsername)
# cd

3) Download the file 
# wget [http://gdesklets.zencomputer.ca/NewsGrab-1.5.tar.gz](http://gdesklets.zencomputer.ca/NewsGrab-1.5.tar.gz)

3) Decompress the file
# tar -zxvf NewsGrab-1.5.tar.gz

4) Copy the controllers in the correct location (this was the problem)
#  cp -r NewsGrab/controls/NewsGrab .gdesklets/Controls/

5) Now copy the whole directory to the Display location
# cp -r NewsGrab .gdesklets/Displays/

6) You can now remove the file downloaded and the folder decompressed (if you want)
# rm -rf NewsGrab NewsGrab-1.5.tar.gz

In this point the program should be correctly installed but maybe it's no work unless you restart the session or restart the computer. If you can restart the computer do it to be sure :)

PD: Sorry for my English

---

