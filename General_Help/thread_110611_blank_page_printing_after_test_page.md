---
title: "blank page printing after test page"
date: 2005-12-31
forum: General Help
---

### Post by ajaustin on 2005-12-31
When I print a test page, either Ubuntu or CUPS, the test page prints and then a blank page is fed.  Also if I print a document from OpenOffice I get the extra blank page unless I print 2 pages in which case there is no blank one.

I have 2 computers with Ubuntu and the one I first set up did this briefly when I first installed the printer - HP LaserJet 4, PostScript on JetDirect, but then it magically sorted itself out.

The second computer does not seem to want to sort itself out and continues putting out a blank page.  I have checked all the configurations that I can find in both the GUIs and /etc/cups and everything seems identical on both computers.

Any suggestions?

Tony

---

### Post by Sef on 2006-01-04
I posted the below earlier.  Hope it helps you.

Check out this post, I helped me to get my printer working:

[http://ubuntuforums.org/showthread.p...light=PSC+1600](http://ubuntuforums.org/showthread.p...light=PSC+1600)

From it, Wondering Jew wrote in part (about his 1610 PSC)


Quote:
sudo apt-get install hplip gtklp xpp hpijs python-qt3-doc libqt3-mt-mysql hplip-ppds

I don't know if you need all those packages they were all reccomended or suggested and I hate going back and adding things later... then I went to system->administration->printing > printer> add printer and in step 2 I selected psc 1600 from 'HP (HPLIP)' in the manufacturer drop down menu (as opposed to just 'HP' which did make a difference for me ) this got the printing part working.

---

