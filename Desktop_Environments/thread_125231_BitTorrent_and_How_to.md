---
title: "BitTorrent and How to"
date: 2006-02-03
forum: Desktop Environments
---

### Post by utab on 2006-02-03
Hi 

Could u please explain a bit about Torrents and how to use them for file sharing and download purposes. The complete steps are appreciated.

Thx.

---

### Post by Thulemanden on 2006-02-03
he, he, some request.

 [LEFT] 	 		[[IMG]http://www.bittorrent.com/images/bittorrent_lg.gif[/IMG]]("http://www.bittorrent.com/index.html") 	
   	 		[Home]("http://www.bittorrent.com/index.html")
         [Introduction]("http://www.bittorrent.com/introduction.html")
 		[documentation]("http://www.bittorrent.com/documentation.html")
 		[FAQ]("http://www.bittorrent.com/FAQ.html")
 		[donate!]("http://www.bittorrent.com/donate.html")

		 	
    	 			Documentation : Guide
                    [Guide]("http://www.bittorrent.com/guide.html") | [Protocol]("http://www.bittorrent.com/protocol.html") | [Paper]("http://www.bittorrent.com/bittorrentecon.pdf") 
                     This is a how-to for making files publicly available via BitTorrent, and it's primarily written for people running Windows. But even if you're not running Windows, the steps you need to do are quite similar, and you can find further instructions in README.txt in the source distribution. 
                     1. Install BitTorrent on your machine 
                     [INDENT]                       If you're reading this you've probably                       installed BitTorrent already, but if not get it                       from the [homepage]("http://www.bittorrent.com/index.html"). 
                      [/INDENT]                     2. Get a tracker
                     [INDENT]                       You need a tracker for downloaders to be able to find each other. Because of this central role, a tracker should be on a very reliable Internet connection. Therefore it's strongly recommended that you use a tracker running on a stable server system (as opposed to your unstable Windows desktop system). 
                       Everyone else making files available via BitTorrent is using a tracker, and a single tracker can handle a huge number of files with very little load. So you could ask others for the URL of their trackers. (Tracker URL is contained in .torrent files.) However, you should never use anyone's tracker without the owner's permission. That would be rude. 
                       If you want to set up your own tracker, follow the instructions in the README.txt in the source distribution. 
                     [/INDENT]                     OR
	                      2. Create a trackerless (DHT) torrent
                     [INDENT]                       If you decide to create a trackerless (DHT)                       torrent, you do not need a tracker URL.  Just                       choose "Use DHT" in step 4.
                     [/INDENT]                     3. Get a web server 
                     [INDENT]                       Any web server will do, but you must associate the extension .torrent with the mimetype application/x-bittorrent . You should ask your web server's administrator to set it up. 
                       If you are the web server administrator, either add the line 
                       AddType application/x-bittorrent .torrent 
                       To httpd.conf , or 
                        application/x-bittorrent .torrent 
                       to mime.types . 
                     [/INDENT]                     4. Make .torrent files
                     [INDENT]                       Launch "Make Torrent" from the Start menu, or                       maketorrent.exe from C:\Program                       Files\BitTorrent\maketorrent.exe.
  	              Add the file that you want to make a .torrent 	              for.  If you want to put many files into a 	              single torrent, put all of those files into a 	              directory, and add that directory.
  	              Enter the tracker URL (see step 1), or select 	              "Use DHT" if you want to make a trackerless 	              torrent.
                        Click the 'Make' button and .torrent files                       will be created. For a file named spam,                       a file named spam.torrent will be                       created. 
  	              Newer versions of the BitTorrent torrent 	              creator have a button to automatically "Start 	              seeding" the torrent you have just created. 	              Click this button.
                     [/INDENT]                     5. Put the .torrent files on your web server 
                     [INDENT]                       Do this however you normally put files on your web server, for .torrent files are just ordinary static files. 
                     [/INDENT]                     6. Start a complete downloader 
                     [INDENT]                       For people to be able to download it is necessary that there be at least one downloader which has everything to begin with. Enter the URL you put the .torrent file at into your web browser, and select the complete local file (or directory) as the location to save to. After checking that the integrity of the file(s), the downloader will report that the download has succeeded, and wait for peers to upload to. 
                       If there are multiple files you'd like to distribute, and they're not grouped into a single .torrent, you have to start a separate downloader for each .torrent file. 
                       It is essential that your complete downloader be able to receive incoming connections. If you're behind a firewall or NAT, you should forward ports 6881 through 6889 to your machine. (The first downloader uses 6881, the next 6882, etc. The range is configurable.) 
                     [/INDENT]                      7. Link to the .torrent file
                     [INDENT]                       You can link to the .torrent file using an ordinary hyperlink. Sending the URL in email also works.
                     [/INDENT]                     8. **Have fun! **
                     
                    
  	
   [/LEFT]
    		 			
			BitTorrent, its logo and its web site are all copyright © 2001-2005 BitTorrent, Inc.

[http://www.bittorrent.com/guide.html](http://www.bittorrent.com/guide.html)

---

