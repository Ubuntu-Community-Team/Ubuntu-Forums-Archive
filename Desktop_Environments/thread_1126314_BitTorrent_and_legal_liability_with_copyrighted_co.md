---
title: "BitTorrent and legal liability with copyrighted content"
date: 2009-04-15
forum: Desktop Environments
---

### Post by finite9 on 2009-04-15
I live in Sweden, and many of you have probably heard about the recent law change that lets MPAA/RIAA get information from ISPs about suspected downloaders.

I was always under the impression that it was those using eDonkey eMule etc, or other clients that shared a users hard drive that were under the most threat, as it was easy to logon to those networks and see what was being shared.  With BitTorrent on the other hand, downloading the torrent file is not illegal in itself, although it is easy to enable Tor button in Firefox to hide your IP whilst getting the torrent metafile, and getting the actual torrent from several different sources, one piece at a time, was very hard to prove or identify, or so I thought.

Now I am not so sure.  Can someone identify that I have downloaded a film by gathering the traffic details from every peer I was connected to?  Does it have to be proven that I downloaded the entire file or is it enough that one peer is identified that was sharing on 50k piece of a film (for example)?

I used to think that the only way for MPAA to get me was to get details from the torrent site that I had downloaded the torrent file from an IP i was assigned at that time.  Now I suspect that it is very easy to gather all the stats about all peers I have downloaded content from.

Doesn't encryption within the bittorrent client solve this problem?  Why do I need SwarmScreen as well?  So what if an ISP can identify the pattern of my downloading habits, the content is still encrypted right?

I would not class myself as a heavy downloader, but I love getting episodes of TV shows that I have missed on TV or cannot get on my TV.  Yes, it's legally wrong, but there you go.

Im not interested in getting into discussions of moral right, legal right and whatnot, just the facts about what can be traced and how easy it is to trace illegal content with bittorrent and if there are any methods to get around it.

---

### Post by The_Doc_tor on 2009-04-15
):P  Hi, Hello yes I see your point & I have no idea what is possible but I do think posting a confession as you have done onto a forum on the web is a first class way to get caught out.

I suspect that 9.995 Times out of 10 it is more likely that copyright enforcement agencies get there information through admissions of guilt like the one you just posted or through sheer smugness & bragging over email, blogs & web forums.

Why work hard at catching downloaders when they stick their hand up and say "I Know what I am doing is illegal but I still do it"

Just a thought?????

---

### Post by Jakey_TheSnake on 2009-04-15
^ Because they'd have to filter through 99% of their web traffic (regular), and then visit all the sites manually themselves, as opposed to just noticing the type of incoming connection that goes with BitTorrent'ing, that's why. 

Unfortunately though, I can't answer the OP's question.

---

### Post by Psychopump on 2009-04-15
When I was using XP, I used PeerGuardian2 which blocked my IP from all kinds of probes. Is there anything like that for ubuntu?

---

### Post by finite9 on 2009-04-16
> **The_Doc_tor said:**
> ):P  Hi, Hello yes I see your point & I have no idea what is possible but I do think posting a confession as you have done onto a forum on the web is a first class way to get caught out.

I suspect that 9.995 Times out of 10 it is more likely that copyright enforcement agencies get there information through admissions of guilt like the one you just posted or through sheer smugness & bragging over email, blogs & web forums.


Im not that worried.  Saying that you done something, and having it proven after the fact are two very different things.  With no criminal record, no previous investigations by MPAA/RIAA, there would be no reason to investigate someone for posting on a forum that they download TV shows.  The people they go after *tend* to be heavy downloaders who have massive traffic in and out and who are easily identifiable.  If someone like that posted that they were sharing out the last Wolverine film for instance, then yeah, it would prompt an immediate investigation.  But TV shows?  Come on!  On a sidenote, I wonder what the case would be if I said I paid my TV licesne and had legal right to watch that TV show?  "oh but thats streamed on TV, not stored on your hard drive"... Yeah but I record it from TV onto my PVR and then have the ability to take out the hard drive from my PVR and save the contents onto my PC quite legally, if I wanted to, so the fact I have the TV show store on disc becomes irrelevant.  In fact, until a year or two ago, in Sweden, it was *legal* to download and only illegal to share out.  Admittedly, you're sharing when you use bittorrent anyway, but it's a damn sight harder to prove than with those networks that share your hard drive.

Think about it a moment.  If you used the old Kazzaa, and shared out 50GB of your hard disc with copyright material, the MPAA could just logon to Kazzaa themselves, identify your computers IP address, see exactly what you were sharing and go to your ISP and get them to hand over your name and address then prosecute you.  It would be trivially easy for them to use this method of identification.

With Bittorrent, there is no central network point.  Everyone is a server and you cannot identify a downloader simply by monitoring what he downloads from a torrent site like Pirate Bay.

Do you realise what resources would be involved to identify a bittorrent user?  You would have to catch them in the act and if they only caught the last 50 MB of a file, they could not neccessarily prove that it was the whole file you were sharing...it could be a compilation or newly generated piece using parts of copyrighted material, which could be defined as fair use if that were true, and then they would have no case.  MPAA could possibly download a torrent they wanted to catch people downloading, and just set it going and collect IPs of all those sharing, but if they only get 50MB from everyone, can that really stand up in court that the whole file has been shared by that person?


Hmmm.  Suppose I just answered my own question.  SwarmScreen and encryption dont mean jack if MPAA lawyer simply logs on gets torrent file and then catches all IPs of those sharing the file.  Encryption would be in effect between his and your computers, but *he* can still see who you are via your IP.  The resources required for this would be enourmous.

By the way, does anyone actually know how they identify people???

Encryption might stop an ISP from traffic shaping, or stopping agencies from mass monitoring an ISP to see who is sharing copyright material, but doesn't stop an agency downloading directly from you.

The only way is to completely mask your IP.  I have never used Tor for this as it completely shits on their network and that was not the intended use, but I think there are other services that can mask your IP, so I suppose IP masking (not using Tor) in combination with encryption built into the torrent client would be adequate.

---

### Post by constantine lotek on 2009-09-21
hello, 

i am also concerned about this issue. i hate the fact that they are out there spying on us. i found a pretty good article here: [http://lifehacker.com/372633/protect-your-privacy-when-downloading](http://lifehacker.com/372633/protect-your-privacy-when-downloading) .

but i've been looking around and an't find the linux answers that are mentioned in the article. even though one can never be completely safe the article suggests using peerguardian2 and BT Guard for added protection. Surely there is some good linux stuff out there. where is it?

---

### Post by bobince on 2009-09-22
PerrGuardian2 is a complete waste of time. It will not help you avoid any agency looking for copyright infringements today. There was a period when they used their own networks to do this monitoring, and for that brief time PG2 was effective. That time is long gone. They now come in from quite normal home DSL IP addresses which PG will not be able to block.

BTGuard is simply a proxy service; there are many different proxy and VPN providers that will work fine from any OS.

---

### Post by Subban on 2009-09-22
The agencies that collect the data for the *AA simply connect to the torrent  appearing as a normal peer, however their application appears to log IP's and time/data that your client is on the swarm and making available the data they are interested in (movie/music or whatever) whilst they downlaod the file. This is then logged and made available to the *AA to persue.

The *AA if then inclined (and mostly they sure as hell are) lookup the IP and head off to the court house for a John Doe warrant thingy (normally only issued in cases where a criminal case is likely to be brought as best I know), this is then used to ask the ISP that the IP belonged to give up the details on which poor sucker has the IP at that given time. The ISP is obliged to coorperate due to the warrant thing, the *AA then have your details to hand to their attack dogs and persue a purely civil matter (remember the criminal case bit before...)

Essentially at that point you are buggered, they have you logged on thier forensic* software sharing the file, they have your ISP linking you to the IP. If you are guilty of what they say, then you need to speak to a lawyer pretty fast, if you genuinely are not guilty then best speak to one anyway and protest your innocence. They do make mistakes the classic is the elderly couple accused of downloading hardcore gay pornography, or the elderly lady who living alone I believe was accused of downloading gangsta rap she had never heard of.

Best thing, stay off public trackers, use a seedbox/vpn, switch to newsgroups. At least one case heading towards court I believe is a woman accused of sharing some music, but was actually using a "leech" client, it was hacked in such a way as to not upload. If it couldn't upload then she wasn't sharing. It will be interesting to see how that goes if it has its day in court.

*the software has never been peer reviewed or had its accuracy qualified by any third party, so make of that what you will.

Anyways, I am not a lawyer but I have been concerned about these matters for a long time and regularly read information on the subject at p2p.net, slyck and torrentfreak blogs.

---

