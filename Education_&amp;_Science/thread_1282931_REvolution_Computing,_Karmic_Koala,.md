---
title: "REvolution Computing, Karmic Koala, ???"
date: 2009-10-04
forum: Education &amp; Science
---

### Post by gunksta on 2009-10-04
For those who don't follow Ubuntu development carefully, the first Beta for the 
next Ubuntu was recently released, so I took my home system and upgraded to 
help out with filing bugs, etc. 

Today, when I loaded an R session I had developed before the upgrade, I saw 
something new in my R "welcome message".
```


R version 2.9.2 (2009-08-24)
Copyright (C) 2009 The R Foundation for Statistical Computing
ISBN 3-900051-07-0

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.


This is REvolution R version 3.0.0:
the optimized distribution of R from REvolution Computing.
REvolution R enhancements Copyright (C) REvolution Computing, Inc.

Checking for REvolution MKL:
- REvolution R enhancements not installed.
For improved performance and other extensions: apt-get install revolution-r

```

The last part, about this being the "enhanced" version of R was . . . 
unexpected.  I have heard of this company before and now I've spent some time 
on their website. Looking at my installation, Ubuntu did not install any of 
the REvolution Computing components, although R now basically thows a warning 
every time I start it.

Does anyone here have any experience with REvolution Computing? I think it's great that their stuff is now easily available in Ubuntu, although I'm a little annoyed that I'm effectively getting commercials now when I try to use R. My question(s) for the community is this (pick any question(s) you'd like to answer: 
        [LIST=1]
[*]Should I install the REvolution Computing packages? 
[*]        Do these packages really make R faster? 
[*]        Are these packages stable? 
[*]        What are your experiences with REvolution Computing software?
[*]        Why is there a commercial in my Ubuntu?
[/LIST]

I asked a similarly worded question on the R-users mailing list. If I get any interesting responses I will link to them or cut and paste them here to make them available to this community too, for folks who don't follow both.

---

### Post by machoo02 on 2009-10-05
This is interesting, because they don't list a Linux version on their website.  Only Windows and OSX.

---

### Post by gunksta on 2009-10-05
This is what I've gotten so far, from REvolution Computing. It sounds like a pretty good answer to me. This is cut from the R-Users mailing list. I've posted the gentleman's contact info and what not here, since it is publicly available on the mailing list and is an easy Google/Nabble Search away.

-----------------------------------------------------------------------------------
From: David M Smith <david@revolution-computing.com>
Re: [R] Ubuntu, Revolutions, R

Andrew is correct: the upcoming release of Ubuntu (Karmic Koala) will
feature the REvolution R distribution. (I am a REvolution Computing
employee.) Our developers have been working with Canonical's
representatives over the past several months to upgrade R in Ubuntu to 2.9.2 and to include the REvolution R extensions.

> My question(s) for the community is this (pick any question(s) you like to
> answer:
>        Should I install the REvolution Computing packages?
>        Do these packages really make R faster?
>        Are these packages stable?
>        What are your experiences with REvolution Computing software?

Whether you install the REvolution Computing packages is up to you.
When you upgrade to KK, the only change made to stock R is the
.Rprofile.site file, adding the message about how to install the
extensions. (You can edit the .Rprofile.site file if you prefer.)

If you do install the extensions, no changes are made to the core R
language (it is 100% compatible with stock R). R will be linked to
multi-threaded math libraries, which will improve performance for some mathematical operations (particularly on a multi-core system, where more than 1 processor will be used). So you should expect it to make R faster.

Installing the extensions also installs some additional packages from
REvolution Computing, including foreach and iterators, and Simon
Urbanek's multicore package from CRAN. The REvolution packages have been in use for over a year, and are very stable. In any case they are not attached by default. But if you do load these packages, you can
use the "foreach" function to parallelize loops, making R run faster
on multicore systems.

I'll leave others to speak of their experiences of REvolution
Computing software (our contributions to the community include the
packages nws, foreach, iterators, doSNOW and doMC and REvolution R
itself). But from my personal perspective, I'm proud to have been able
to extend awareness and use of R to new domains, and to improve the
performance of R for many users.

# David Smith
Director of Community, REvolution Computing

David M Smith <david@revolution-computing.com>
Director of Community, REvolution Computing [www.revolution-computing.com]("http://www.revolution-computing.com")
Tel: +1 (206) 577-4778 x3203 (San Francisco, USA)

Check out our upcoming events schedule at [www.revolution-computing.com/events]("http://www.revolution-computing.com/events")

---

### Post by earlycj5 on 2009-10-05
Thanks for the information gunksta.

I installed their multithread packages on an OpenSUSE workstation where I compiled ATLAS and R for the machine, a dual quad-core Xeon with 20gb RAM.

Be interesting to see if I can get any performance gains from them.

I know about REvolution R previously, David is quite active on Twitter, #rstats.

---

### Post by ahmatti on 2009-10-06
gunksta,
Thanks for posting this too. I have given up on trying beta versions of Ubuntu after some bad experience in the past, but I'm looking forward to testing this when Karmic comes out. 

If you do give the REvolution computing packages a try, let us know what you think. I have tried to run some parallel computations using the "snow" package, but I really didn't get any benefits with my dual core laptop, but the code did run significantly faster on a linux cluster. I think the limiting factor on my laptop was the hard disk, because I had quite a big data set.

---

### Post by gunksta on 2009-10-06
I do intend to install the new packages, but I too will need to wait until Karmic is complete. My work computer is . . . . inadequate . . . . for some tasks and I am careful to keep my work environment and home environment compatible, which is one of the reasons I was concerned with the new message when I started R.

Note - I suppose it's fair to say that I should own the responsibility of any breakage in my system since I _did_ upgrade my home system voluntarily.

I doubt I see any improvement on my laptop, but I do expect to see some improvement on a few things on my system at home. Sadly, I don't have access to a cluster so I can't check that (perhaps I need to go out and buy up a handful of original style PS3s).

---

### Post by gunksta on 2009-10-19
I thought I would link to this announcement from REvolution Computing.

[http://blog.revolution-computing.com/2009/10/revolution-r-coming-to-ubuntu.html](http://blog.revolution-computing.com/2009/10/revolution-r-coming-to-ubuntu.html)

**October 19, 2009**

    			**REvolution R coming to Ubuntu**

 	 	 		 			REvolution Computing's enhanced distribution of R, REvolution R, has been available for [free download ]("http://http//revolution-computing.com/downloads/revolution-r.php")from our website for Windows and MacOS for over a year now, and has been used by thousands of R users for high-performance statistical data analysis. Soon, we'll be expanding our free distributions to [Ubuntu Linux]("http://www.ubuntu.com/"), with the release of [REvolution R 3.0]("http://revolution-computing.com/products/revolution-r.php").
 Like the Windows and MacOS versions, REvolution R 3.0 for Ubuntu Linux includes performance enhancements that make common mathematical operations (like matrix multiplication and decomposition) [faster than in regular R]("http://revolution-computing.com/products/r-performance.php").  These optimized math libraries are also multi-threaded, so if you're using a multi-CPU or multi-core workstation or laptop, REvolution R will use all available CPUs for many mathematical operations.
 REvolution R 3.0 also features new parallel programming tools for R, so you can write loops in R which run faster by using multiple CPUs simultaneously. The new "[foreach]("http://blog.revolution-computing.com/2009/07/simple-scalable-parallel-computing-in-r.html")" function acts as a replacement for the "for" loop and function like "lapply", while the "doMC" function enabled multiple iterations of the loop to run simultaneously. 
 REvolution R 3.0 is 100% compatible with the most recent version of R (R 2.9.2), so all the scripts and packages you currently use with R will produce exactly the same results in REvolution R 3.0 (although they may take less time to run).
 When the new 9.10 release of Ubuntu Linux (codenamed "Karmic Koala") is released on October 29, REvolution R will be immediately available as a download from the Ubuntu repositories. (If you're already using the Karmic beta release, it's available right now.) You can install REvolution R for Ubuntu by entering the following command:
 [FONT=Courier]sudo apt-get install revolution-r[/FONT]
 If you already have R installed in Ubuntu (or only install the [FONT=Courier]r-base-core[/FONT] package), when you upgrade to Ubuntu 9.10 you'll see the following message when starting R:
 [FONT=Courier]REvolution R enhancements not installed.  For improved
performance and other extensions: apt-get install revolution-r[/FONT]
 [Some technical information for Ubuntu junkies: the "[FONT=Courier]revolution-r[/FONT]" package builds on the "[FONT=Courier]r-base-core[/FONT]" package so that they can both share other R-related package dependencies (like all the CRAN packages), which saves time for the volunteer maintainers of the upstream packages. Other than the message above, the [FONT=Courier]r-base-core [/FONT]package is otherwise unmodified in 9.10, and if you wish you can suppress that message by modifying the [FONT=Courier]Rprofile.site[/FONT] file.]
 We're very excited to be expanding the supported platforms of REvolution R to Ubuntu Linux, and we hope that the performance improvements and parallel computing tools make R even better for many users. Thanks go to our friends at Canonical for helping us introduce REvolution R to Ubuntu, and special thanks go to Debian developer and R contributor Dirk Eddelbuettel for invaluable technical assistance in creating and submitting the REvolution R packages for Ubuntu.
 By the way, if you have any questions about using any of the REvolution R distributions, don't forget you can always ask questions in our [REvolution R forums]("http://forums.revolution-computing.com/") where other REvolution R users and our technical staff are ready to help.

---

### Post by earlycj5 on 2009-10-19
Just to follow up on my previous post.

I don't have much use for the foreach package and the like but another grad student in my lab does and reported that it greatly improved the efficiency of some of his programs.

*edit* Talked with him yesterday, 7X speed increase was what he reported on an 8 core machine with 20Gb RAM.

---

### Post by purgatori on 2009-10-31
Are there any benefits for non-multi-core users?

---

### Post by earlycj5 on 2009-11-01
> **purgatori said:**
> Are there any benefits for non-multi-core users?

If there are they won't be as great.

You could contact David and inquire.

---

### Post by frdrx on 2009-11-06
The r-base-core package has been turned into adware. I am not willing to put up with advertisements for proprietary software in free-software packages. I hope I'm not alone and that the community will speak up loudly against this unacceptable practise.

---

### Post by gunksta on 2009-11-06
> **frdrx said:**
> The r-base-core package has been turned into adware. I am not willing to put up with advertisements for proprietary software in free-software packages. I hope I'm not alone and that the community will speak up loudly against this unacceptable practise.

I got curious and looked at the license and you are right. It's not an OSS license. This is a curious situation. My first reaction is to agree with frdx, but I do have Flash installed on my machine so I can watch YouTube videos and other Internet media. If you don't have Flash installed, FireFox will encourage you to install Flash, so I would argue that there is precedence for Free Software to advertise / recommend non-free software. When Gnash gets better I'll use it, but last time I installed Gnash it nearly melted my processor.

In all honesty, I don't have a problem with Canonical working with companies to distribute non-Free software. I for one do not have an innate moral opposition to the existence of non-Free Software just as I do not have an innate moral opposition to smoking. That being said, I do believe that it is my right to not smoke and to avoid the use of non-Free Software. In other words, I don't want to tell others what to do but at the same time don't want people telling me what to do. (I _do_ have a libertarian streak in me.)

I think the best place for something like Revolution's products are in the App Center. I think a well designed App Center should help users discover related applications (Free and non-Free) but the license should be clearly displayed so end-users can make an informed decision for themselves.

For the time being I'm going to yank Revoloution-R off my machines. It looks like some of the underlying technology is available as Free Software and I have to admit that I have not noticed an increase in speed in most of my scripts. But, I agree that the base installation shouldn't be advertising for a non-free product. I think the best approach at the moment is to work with Canonical and see if there is some way to move the advertisement aspect to somewhere else in the stack.

------------------ License from r-revolution-revobase -----------------

REVOLUTION COMPUTING End User License Agreement

IMPORTANT-READ CAREFULLY: THIS END USER LICENSE AGREEMENT (THE “AGREEMENT”) IS A BINDING AGREEMENT COVERING YOUR USE OF the REVOLUTION COMPUTING (“REVOLUTION COMPUTING”) SOFTWARE (the “SOFTWARE”).  BY ACCESSING OR USING THE SOFTWARE AND ANY ASSOCIATED MEDIA, PRINTED OR ELECTRONIC USER MANUALS OR GUIDES OR INSTRUCTIONS REGARDING USE OF THE SOFTWARE (THE “DOCUMENTATION”), YOU (THE “LICENSEE”) AGREE TO ALL THE TERMS OF THIS AGREEMENT REGARDING YOUR USE OF THE SOFTWARE AND DOCUMENTATION.  IF YOU DO NOT AGREE WITH ALL OF THESE TERMS, DO NOT ACCESS OR USE THE SOFTWARE.  LICENSEE HAS NOT BECOME A LICENSEE OF, AND IS NOT AUTHORIZED TO USE OR DISTRIBUTE THE SOFTWARE UNLESS AND UNTIL IT HAS AGREED TO BE BOUND BY ALL THESE TERMS.  THE “EFFECTIVE DATE” FOR THIS AGREEMENT SHALL BE THE DAY LICENSEE FIRST ACCESSES THE SOFTWARE.
1.LICENSE GRANT.  Subject to the terms and conditions of this Agreement, REvolution Computing grants to Licensee, solely during the Term (defined below), a non-exclusive, non-transferable, revocable, non-sublicensable, fully paid-up, limited license to use, improve and redistribute the Software (in binary form only) in any manner consistent with the terms and policies under which the Ubuntu operating system is distributed.
2.NO OTHER RIGHTS.  Except as expressly set forth in Section 1, no licenses of any kind are granted hereunder, whether by implication, estoppel or otherwise.  Without limiting the generality of the foregoing, you will not, nor permit any third party to translate, reverse engineer, decompile, disassemble (except to the extent that this restriction is expressly prohibited by law) or otherwise attempt to discover the source code of all or any portion of the Software or remove any proprietary markings, copyright, notices, logos, trademarks, trade names or labels on the Software and/or Documentation.  To the extent that any of the foregoing restrictions in this Agreement do not comply with the terms and policies under which the Ubuntu operating system is distributed, such restrictions in this Agreement will not apply.
3.Third Party Software. Certain third party components provided in or with the Software (“Third Party Components”) are subject to various other terms and conditions imposed by the licensors of such Third Party Components.  Licensee may view the relevant licenses and /or notices for such Third Party Components at [[www.revolution-computing.com/__________]](www.revolution-computing.com/__________]).  Licensee’s use of the Third Party Components is subject to and governed by these Third Party Component licenses, except that this Section 3 and Section 8 (No Warranty) and Section 9 (Limitation of Liability) of this Agreement also govern Licensee’s use of the Third Party Components.  Licensee agrees to comply with the terms and conditions contained in all such Third Party Component licenses.
4.FEES.  Subject to the terms of this Agreement, the Licensee shall have the right to use the Software free of charge during the Term.
5.NO SUPPORT.  The license granted under this Agreement does not include the right to receive any support for the Software by REvolution Computing.
6.OWNERSHIP.  All right, title and interest in and to the Software, any intellectual property embodied therein, and any improved, updated, modified or additional parts thereof shall at all times remain the property of REvolution Computing and its third party licensors, as applicable.  Nothing herein shall give or be deemed to give Licensee any right, title or interest in or to the same, except as expressly provided in this Agreement.  All rights not expressly granted to Licensee are hereby reserved by REvolution Computing and its third party licensors.
7.CONFIDENTIALITY. Licensee acknowledges that Licensee may have access to, and REvolution Computing may disclose to Licensee, certain information that REvolution Computing considers confidential and proprietary concerning the Software, including, without limitation, information regarding the development and functionality of the Software, or any part thereof (“Confidential Information”).  Licensee agrees not to use the Confidential Information for Licensee’s own benefit or the benefit of any third party.  Licensee further agrees not to disclose the Confidential Information to any third party.   Licensee shall have no obligation of confidentiality for any Confidential Information that: (i) now or hereafter becomes generally known or available through no act of Licensee; (ii) is known by Licensee without restriction on disclosure at the time Licensee receives such Confidential Information from REvolution Computing, as evidenced by written records; (iii) is hereafter furnished to Licensee by a third party without restriction on disclosure; or (iv) is independently developed by Licensee without use of or reference or access to the Confidential Information.
8.NO WARRANTY.  Licensee agrees that neither REvolution Computing nor any of its third-party licensors nor their agents or representatives shall be responsible for loss, destruction, or alteration of programs, data and other information resulting from Licensee’s use of the Software.  LICENSEE expressly acknowledgeS and agreeS that the use of the Software is at LICENSEE’S own risk.  THE SOFTWARE IS PROVIDED TO LICENSEE ON AN “AS IS” BASIS and without any warranty of any kind.  REVOLUTION COMPUTING expressly disclaims all warranties, express, implied, statutory or otherwise, including without limitation, the implied warranties of merchantability, fitness for a particular purpose and noninfringement of third party rights.  REVOLUTION COMPUTING does not warrant that the functions contained in the SOFTWARE will meet LICENSEE’S requirements, or that the operation of the SOFTWARE will be uninterrupted or error-free, or that defects in the software will be corrected.  no oral or written information or advice given by REVOLUTION COMPUTING or its authorized representatives shall create a warranty.  some jurisdictions do not allow the exclusion of implied warranties, so the above exclusion may not apply to LICENSEE.
9.LIMITATION OF LIABILITY.  IN NO EVENT SHALL REVOLUTION COMPUTING BE LIABLE TO LICENSEE OR ANY OTHER THIRD PARTY FOR ANY DIRECT, INDIRECT, SPECIAL, PUNITIVE INCIDENTAL OR CONSEQUENTIAL DAMAGES ARISING OUT OF OR IN ANY WAY RELATED TO THE SOFTWARE OR THIS AGREEMENT, INCLUDING, WITHOUT LIMITATION,  LOST PROFITS, DATA, OR BUSINESS OPPORTUNITY, REGARDLESS OF THE FORM OF ACTION, WHETHER IN CONTRACT, TORT (INCLUDING NEGLIGENCE), STRICT PRODUCT LIABILITY OR OTHERWISE, EVEN IF REVOLUTION COMPUTING HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.  SOME STATES OR OTHER JURISDICTIONS DO NOT ALLOW THE EXCLUSION OF LIMITATION OF LIABILITY FOR INCIDENTAL OR CONSEQUENTIAL DAMAGES, SO THE ABOVE LIMITATIONS AND EXCLUSIONS MAY NOT APPLY TO LICENSEE.  REVOLUTION COMPUTING’S LIABILITY IN SUCH JURISDICTIONS SHALL BE LIMITED TO THE EXTENT PERMITTED BY LAW.
IN NO EVENT SHALL REvolution Computing’s TOTAL, AGGREGATE LIABILITY ARISING FROM OR IN ANY WAY RELATED TO THE SOFTWARE OR THIS AGREEMENT EXCEED FIVE HUNDRED DOLLARS (US$500).

THE PARTIES AGREE THAT THESE LIMITATIONS SHALL APPLY EVEN IF THIS AGREEMENT OR ANY LIMITED REMEDY SPECIFIED HEREIN IS FOUND TO HAVE FAILED OF ITS ESSENTIAL PURPOSE.
The sections on limitation of liability and no warranty allocate the risks in the Agreement between the parties.  This allocation is an essential element of the basis of the bargain between the parties.
10.TERM AND TERMINATION.
10.1Term.  This Agreement is effective as of the Effective Date, and will continue in effect unless otherwise terminated pursuant to the provisions herein (“Term”).
10.2Termination.  Licensee may terminate this Agreement for any reason or no reason, at any time, by ceasing all use of the Software and Documentation.  This Agreement will terminate immediately without notice from REvolution Computing if Licensee fails to comply with any provision of this Agreement
10.3Effects of Termination.  Upon termination of this Agreement, (i) Licensee shall immediately cease using the Software and Documentation, and (ii) Licensee shall certify in writing to REvolution Computing, upon REvolution Computing’s written request, that Licensee has destroyed all documents and other tangible items that Licensee has received or created pertaining, referring or relating to the Confidential Information of REvolution Computing and its third party licensors.
10.4Survival.  Except for Sections 1 (“License Grant), 10.1 (“Term”), and 10.2 (“Termination”), all Sections of this Agreement shall survive termination.
11.Restricted Rights.  The Software under this Agreement is “commercial computer software” as that term is described in DFAR 252.227-7014(a)(1).  If acquired by or on behalf of a civilian agency, the U.S. Government acquires this commercial computer software and/or commercial computer software documentation subject to the terms of this Agreement as specified in 48 C.F.R. 12.212 (Computer Software) and 12.11 (Technical Data) of the Federal Acquisition Regulations (“FAR”) and its successors.  If acquired by or on behalf of any agency within the Department of Defense (“DOD”), the U.S. Government acquires this commercial computer software and/or commercial computer software documentation subject to the terms of this Agreement as specified in 48 C.F.R. 227.7202 of the DOD FAR Supplement and its successors.
12.GENERAL PROVISIONS. Licensee agrees to use the Software in a lawful manner and in accordance with its intended usage.  Licensee agrees to comply with all export laws and restrictions and regulations of the United States or foreign agencies or authorities, and not to export or re-export the Software, or any part thereof, in violation of any such restrictions, laws or regulations, or without all necessary approvals. This Agreement may not be assigned by Licensee to any other party without the express written approval of REvolution Computing.  Any assignment in violation of the foregoing shall be void.  This Agreement shall inure to the benefit of the parties’ respective successors and permitted assigns. All notices shall be in writing and shall be delivered by personal service or by mail at the address of the receiving party set forth in  this Agreement (or at such different address as may be designated by such party by written notice to the other party).  This Agreement shall be governed by and construed in accordance with the substantive laws of the state of Connecticut.  The parties agree the United Nations Convention on Contracts for the International Sale of Goods is specifically excluded from application to this Agreement.  No supplement, modification, or amendment of this Agreement shall be binding unless executed in writing by a duly authorized representative of each party. The parties agree that this Agreement is the entire agreement between the parties  regarding the subject matter hereof and supersedes all previous and contemporaneous agreements, understandings and communications, oral or written, including, without limitation, purchase orders and invoices, relating to the subject matter hereof.  If any provision of this Agreement is held to be invalid or unenforceable, in whole or in part, by a court of competent jurisdiction, such provision shall modified to the least degree necessary to make it legal, valid and enforceable, while retaining to the maximum extent possible the intent of the parties, and all other terms of this Agreement shall not be affected thereby and remain in full force and effect.

---

### Post by gunksta on 2009-11-06
For anyone who may be interested, there is an open bug on this, but to date I don't see any replies from any Ubuntu Devs. I've included my Launchpad comment below.

[https://bugs.launchpad.net/ubuntu/+source/r-base/+bug/433799](https://bugs.launchpad.net/ubuntu/+source/r-base/+bug/433799)

------------------------------------------------------------------------------------------------------------------
           I think it is Canonical's right to enter into agreements with other companies to distribute their software (regardless of the license). That being said I think it is equally important to respect the end-users. I don't like the adware and I especially don't like the fact that the extensions are not clearly labeled as proprietary.
 If this product provides a useful service to someone and they are willing to work within the constraints of the license, I think they should use it. That being said, end-users should be told up front when they are installing non-free software. This message need not be derogatory, but it should make it clear that the license is proprietary.
 I would also like to offer a couple of suggestions here.
 1) I think something like the App Center is a better place to position advertisements for related products. A well designed App Center SHOULD help me find new Free and non-Free software that is related to or similar other applications that I am interested in or have already installed. For example, if I searched for R in the App Center, I think it is reasonable to get a list of base packages that include PSPP, Gretl, and Revolution R, and a few dozen other R extensions. If I am interested in R, it is reasonable to assume I may be interested in these other products as well. As long as the App Center clearly displays the licenes (GLP, Apache, LGPL, Proprietary, etc.), end users can make a well-informed decsion regarding what software to use.
 2) I always thought Java's approach to installation was a good one. The old non-free Java installation made you accept or decline the EULA. This way I was given the opportunity to review the license and decide for myself if I wanted to use it or not. I think this is a good way to install other non-free software such as the Microsoft core fonts, Flash, etc. Make it easy, but also give end-users the opportunity to see the license before installing the software when the license is not a Free Software license.
 3) Remove or at least minimize the advertisement for the stuff in R.

---

### Post by frdrx on 2009-11-06
While agreeing with everything you've written above, gunksta, I would only like to say that Firefox does not nag people into installing flashplugin-nonfree if they already have gnash. I think the situation with the current r-base-core package in Ubuntu is quite unparalleled. Imagine LaTeX advertising Indesign. You don't have to be Richard Stallman to see that it is wrong.

---

### Post by gunksta on 2009-11-06
@ frdx, I agree with you. My first post was a little more stream-of-consciousness than it should have been. Canonical should have handled this differently. Fortunately, we have six months to haggle with Canonical about this before they release the next LTS.

------------------------------------------

I did a little more digging and poking and this is what I've come up with. SOME of the Revolution stuff is OSS and some of it is not. The following 3 packages are not OSS:

[LIST]
[*]revolution-r
[*]r-revolution-revobase
[*]revolution-mkl
[/LIST]

However, revolution-r includes several dependencies which are OSS (I checked, they are all hiding in Universe):

[LIST]
[*]r-cran-multicore
[*]r-cran-dosnow
[*]r-cran-foreach
[*]r-cran-domc
[*]r-base-latex
[*]r-cran-iterators
[/LIST]
This is interesting because Revolution's literature emphasizes their product's ability to improve multi-core/cluster performance. This appears to be provided by the foreach, dosnow and multicore packages. Not only are these packages all in Universe, I found this blog post about them:

[http://blog.revolution-computing.com/2009/07/simple-scalable-parallel-computing-in-r.html](http://blog.revolution-computing.com/2009/07/simple-scalable-parallel-computing-in-r.html)

An apache license is just fine with me. It looks like the part that is proprietary are the improved matrix/operators stuff found in the mkl package. The multi-core part is definitely usable, even if you don't want to use non-Free Software.

---

### Post by gunksta on 2009-11-11
I thought it was worth mentioning that I wrote about this discussion on my blog [here]("http://0b10.blogspot.com/2009/11/revolution-computing-ubuntu-910.html"). David Smith responded to my initial post. Unfortunately, he was not able to leave a comment on my blog, because Blogger wouldn't let him log in (silly computers). He sent me a private email which caused me to write a second entry [here]("http://0b10.blogspot.com/2009/11/revolution-computing-ubuntu-910-example.html").

Ad-ware is something that this community has a very low tolerance for (and this is for a very good reason -  this ain't Windows). But, there is a tension between vendors like REvolution Computing who want to find new users, and wants to work with Linux vendors such as Canonical and end-users who REALLY don't want to get advertisements on their computers.

I think the best way to deal with this tension is via an intelligent App Center that helps users find new, relevant software (open-source, proprietary, and mixed) and helps them make informed decisions based on the number of users using this software and the license. This is an important discussion as Canonical takes steps towards working with more and more independent vendors and brings them into the Ubuntu ecosystem.

---

### Post by tomthumb99 on 2010-05-28
I do not need ad-ware on my R version.  I am reading this post, since I also got the message to install revolution-r.  Now that I find its a third party non-core package, I am greatly disappointed. Gunksta, pls clarify if you support Revolution's ad plug here?  If Revolution looking for a free billboard R and Ubuntu software is not the place.  I will not buy/purchase anything from Revolution on principle.

---

### Post by gunksta on 2010-06-02
Busy Busy Busy.

I've been on the road and not checking threads here at the Ubuntu forums on a regular basis. Sorry for not replying sooner.

AFAIK, this issue has already been addressed. There was considerable concern expressed by the community when the ad was initially added to Ubuntu's default R installation. Fortunately, Ubuntu and Revolution Computing both responded. I just looked at my R prompt carefully (Lucid) and I don't see any ads. 

In my opinion - this is a closed issue.

As I have said in the past, placing an ad into the R prompt was inappropriate and no, I do not support adware on Linux. 

But, for clarity's sake I do want to note that I fully support the partnership between Revolution Computing and Canonical. Revolution Computing releases several interesting and useful extensions to R that are 100% open source. I'll admit that I haven't used them much myself, but that is mostly because the work I do rarely requires that sort of horsepower.

I believe the appropriate place for Canonical & Revolution Computing to "advertise" their relationship is in the Ubuntu Software Center. For example - R and other similar programs can be found under:

*Get Software >> Science & Engineering >> Mathematics*

If you look - there are a lot of choices there. Wow. New users can (and should be) forgiven for feeling a little overwhelmed. I think Canonical would do us all a service if they added a simplified window of "Recommended" software to the software center. For example - there are easily 20+ mp3 players for Linux but there are only a handful that are installed by more than a handful of people. I think Canonical should re-work the software center to highlight these top-tier applications, to help new users find them. The apps which make up this list could be reviewed every release to make sure they are still relevant / the best in the field. Canonical could also use this space to advertise products from partners such as Revolution Computing.

Handled appropriately, I do believe it is possible for Canonical to introduce users to best-of-breed software and software that Canonical and it's partners are invested in. The license of this software should be made clear to users BEFORE they install the software, but otherwise, I think it would be a really great way to move forward. And, by distributing this software via the repos, rather than via random downloads on the net, users can be assured that the software doesn't contain anything nasty like a virus or trojan.

That's my 10 cents.

---

### Post by PGScooter on 2010-06-04
I am using R from the CRAN ppa, which is great because it updates flawlessly. How do I install Revolutions add-ons?

Thanks

---

### Post by gunksta on 2010-06-05
That's a good question. I have no idea.

---

### Post by PGScooter on 2010-06-05
> **gunksta said:**
> That's a good question. I have no idea.

all I had to do was
```

sudo apt-get install revolution-R

```

It does not depend on a specific version of R. In fact, most of them are normal packages that you can get from [http://cran.r-project.org/web/packages/](http://cran.r-project.org/web/packages/)

---

### Post by gunksta on 2010-06-05
I would be careful mixing R versions. I don't know for sure about the Revolution packages, but most R packages don't like to be used with a version of R other than the one they were compiled to work with. It may install, but I'm not sure it will work.

OTOH - I may.

If you are using the default ubuntu repos, then installing R from the repos is perfectly safe. But, if you are using the Revolution Computing stuff, it may bork on you when you try to use it. Not sure. AFAIK know that Revolution R is often an iteration or two behind the leading edge of R, for stability/integration reasons.

---

### Post by PGScooter on 2010-06-05
thank you for the warning gunksta, I'll be careful. I wish there were some tests that I could do but I guess I will know if something goes wrong.

---

