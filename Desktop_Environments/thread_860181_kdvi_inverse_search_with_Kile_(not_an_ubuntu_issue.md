---
title: "kdvi inverse search with Kile (not an ubuntu issue)"
date: 2008-07-15
forum: Desktop Environments
---

### Post by shr2004 on 2008-07-15
Hi,
The problem that I am going to ask is not related to my Ubuntu. But as many of you are expert in linux, thats why asking to get any help.

I am using Kile for latex with kdvi. In my Ubuntu machine the inverse search from kdvi to Kile works fine. I am using another desktop with Linux (Centos) where kdvi is installed and I install Kile as a user. When I run kdvi from command line I get following error message and the kdvi opens.
> 
ScimInputContextPlugin()
WARNING: please edit ~/.scim/global and change /DefaultConfigModule to kconfig

I tried to edit that file, with no result.
I would not mind this, but I cannot inverse search from kdvi to Kile, when I click to go to source line I get following error message:
> The external program

kile '(i delete the exact path).tex' --line 60

which was used to call the editor for inverse search, reported an error. You might wish to look at the document info dialog which you will find in the File-Menu for a precise error report. The manual for KDVI contains a detailed explanation how to set up your editor for use with KDVI, and a list of common problems.
I checked the error which mentioned that 'kile command not found'
I can run kile from command line just by typing kile as it is aliased. I then use 'user defined program' in kdvi to tell the exact path, and still get the same error.
If anyone knows the solution then please drop few comments on how to do it. As it is not a burning issue, I will take it lightly

Cheers

---

