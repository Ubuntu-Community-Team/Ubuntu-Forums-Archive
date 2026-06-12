---
title: "How to fetch arxive.org with JabRef?"
date: 2009-07-13
forum: Education &amp; Science
---

### Post by yuzhu on 2009-07-13
I got a problem with the fetching of arxiv.org while using JabRef 2.5. 

"
An Error Occurred while fetching from OAI2 Source ([http://export.arxiv.org/oai2?verb=oai%3ABethe&metadatdaPrefix=arxiv):]("http://export.arxiv.org/oai2?verb=oai%3ABethe&metadatdaPrefix=arxiv%29:")

Malformed identifier 'oai: arXiv.org:Bethe'
"

Can any one help me? Thanks very much!

---

### Post by hubie on 2009-07-13
Something in the link JabRef is using got messed up, like some things getting dropped due to copying and pasting a string with special characters in it.  I say this because within your link you [don't have any argument for verb]("http://www.openarchives.org/OAI/2.0/openarchivesprotocol.htm#ProtocolMessages"), which should be one of: GetRecord, Identify, ListIdentifiers, ListMetadataFormats, ListRecords, and/or ListSets.

Which paper were you trying to get?  For instance, if you wanted to get [this Bethe paper]("http://arxiv.org/abs/hep-ph/9212204"), your request URL would look something like:
[URL="http://export.arxiv.org/oai2?verb=GetRecord&identifier=oai:arXiv.org:hep-ph/9212204&metadataPrefix=arXiv"]```
http://export.arxiv.org/oai2?verb=GetRecord&identifier=oai:arXiv.org:hep-ph/9212204&metadataPrefix=arXiv
```[/URL]

---

### Post by yuzhu on 2009-07-20
Thank you very much.

Basing on your reply, I am now able to fetch arxiv.org with paper ID. :D


> **hubie said:**
> Something in the link JabRef is using got messed up, like some things getting dropped due to copying and pasting a string with special characters in it.  I say this because within your link you [don't have any argument for verb]("http://www.openarchives.org/OAI/2.0/openarchivesprotocol.htm#ProtocolMessages"), which should be one of: GetRecord, Identify, ListIdentifiers, ListMetadataFormats, ListRecords, and/or ListSets.

Which paper were you trying to get?  For instance, if you wanted to get [this Bethe paper]("http://arxiv.org/abs/hep-ph/9212204"), your request URL would look something like:
[URL="http://export.arxiv.org/oai2?verb=GetRecord&identifier=oai:arXiv.org:hep-ph/9212204&metadataPrefix=arXiv"]```
http://export.arxiv.org/oai2?verb=GetRecord&identifier=oai:arXiv.org:hep-ph/9212204&metadataPrefix=arXiv
```[/URL]

---

