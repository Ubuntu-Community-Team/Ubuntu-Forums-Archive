---
title: "Child care administration software"
date: 2011-08-21
forum: Education &amp; Science
---

### Post by heyandy889 on 2011-08-21
Hi, team. This forum looks the most relevant.

I'm a Computer Science student, and I'm communicating with the leader of a non-profit child care provider. Here's the lowdown

* spending too much time digging through their database (using something called "Giftworks")
* database is a bit of a mess. Redundant fields, notes everywhere.

As far as I know, they're looking for a glorified contact list. It would also store some medical data about the kids (most of the kids have disabilities or special needs). 

My best option thus far is to make a custom DB in LibreOffice Base. She is running Windows, but these open source projects tend to be cross platform, at least ones that I follow like LibreOffice, Chromium, and Mozilla Firefox. 

tl;dr
Anyone know of a free, fancy address book?

Thank you!
Nate

---

### Post by kaldor on 2011-08-21
> **heyandy889 said:**
> tl;dr
Anyone know of a free, fancy address book?

Thank you!
Nate

Thunderbird email client? :)

---

### Post by heyandy889 on 2011-08-21
> **kaldor said:**
> Thunderbird email client? :)

A ha! Downloading. *crosses fingers*

---

### Post by SeijiSensei on 2011-08-21
If this organization is in the US, are they covered by HIPAA?  (The childcare agency will almost certainly know if they are.) If so, you need to be aware of the rules governing the privacy of patient health information.  Having just built a PHP-based appointments system for a health center, I had to encrypt all the patient information using AES256 before storing it in the database.

I'd consider a web-based solution myself, using Apache+PHP+PostgreSQL running on a server inside the organization's firewall.  

"Giftworks" sounds like a package that's aimed at fund-raising for nonprofits.  If that's a part of their database needs, I'd take a look at third-party solutions like etapestry.com as well.  No patient data on that site, of course, HIPAA or no HIPAA.  Patient data needs to be maintained separately and protected inside the organization.  I'd use etapestry for things related to fund-raising like donor lists, mass mailings, etc.

---

### Post by Dangertux on 2011-08-21
> **SeijiSensei said:**
> If this organization is in the US, are they covered by HIPAA?  (The childcare agency will almost certainly know if they are.) If so, you need to be aware of the rules governing the privacy of patient health information.  Having just built a PHP-based appointments system for a health center, I had to encrypt all the patient information using AES256 before storing it in the database.

I'd consider a web-based solution myself, using Apache+PHP+PostgreSQL running on a server inside the organization's firewall.  

"Giftworks" sounds like a package that's aimed at fund-raising for nonprofits.  If that's a part of their database needs, I'd take a look at third-party solutions like etapestry.com as well.  No patient data on that site, of course, HIPAA or no HIPAA.  Patient data needs to be maintained separately and protected inside the organization.  I'd use etapestry for things related to fund-raising like donor lists, mass mailings, etc.

I agree with whatever application you choose you should ensure compliance. For more information consult the following [link](http://www.google.com/url?sa=t&source=web&cd=1&ved=0CDQQFjAA&url=http%3A%2F%2Fwww.sans.org%2Freading_room%2Fwhitepapers%2Fhipaa%2Fhipaa-security-compliance-project-identification-logging-auditing-requirements_1227&rct=j&q=HIPAA%20auditing%20standard&ei=PSZRTtbYOpLAtgeTyqHLCQ&usg=AFQjCNFae0H28VikNplEljK1_xrrPN1Iog&sig2=Hz4liN7ZGo-juXIyKsharQ&cad=rja)(it's a pdf)

---

### Post by timlev on 2011-08-29
Looks like part of what she might want is a Student Information System for Health Records, Attendance, and keeping track of IEPs for students with special needs. Here are some open source student information systems:
[http://opensis.sourceforge.net/](http://opensis.sourceforge.net/)
[http://www.ish.com.au/oncourse](http://www.ish.com.au/oncourse)
[http://richtech.ca/openadmin/](http://richtech.ca/openadmin/)
(Demonstration of OpenAdmin - [http://richtech.ca/openadmin/demonstrations.html](http://richtech.ca/openadmin/demonstrations.html))

If she is looking to replace the Giftworks software, she will need a Constituent Relationship Manager (CRM)
Here is an open source CRM:
[http://civicrm.org/](http://civicrm.org/) 

Hope this helps. I would also agree with the above who warn against throwing thowing something together in an unencrypted database. One of these packages above may be a good option.

Good luck!

---

### Post by gunksta on 2011-08-31
While I agree that a web-based tool is possibly the best route, there isn't enough information here to make an informed decision. 

1) Who's data will be stored in the system?
2) What is the nature of the data?

These seem obvious, but they are important questions. If the agency is looking for a Contacts Resource Manager for donors, suppliers, etc. you most certainly do NOT need to worry about HIPAA. I would look at something like [OpenERP]("http://www.openerp.com/"). 

If the data in question is related to clients, HIPAA may or may not be relevant. HIPAA primarily focuses on protecting medical information. Depending on the type of child care provided by this agency, HIPAA may or may not apply. If the agency stores medical records or other sensitive information, HIPAA is probably relevant. And, even if it isn't technically applicable it would not a bad idea to use it as a template for protecting sensitive data. However, if the agency provides after-school care for working mothers, they don't need to worry about HIPAA. You do not have to be HIPAA compliant in order to write down a child's address and mother's name. 

If the agency doesn't deal with sensitive information, don't go down the rabbit hole of HIPAA compliance. Encrypting sensitive data is always good idea (something I wish credit card companies did more often), but HIPAA goes much further and requires written plans for data management including access controls, replication and data destruction. You can't just encrypt a couple of columns in a database and declare HIPAA compliance. If it needs to be HIPAA compliant, out-sourcing development to a firm that writes and hosts HIPAA compliant software is worth considering.

Possibly even more relevant, is the fact that every state has its own collection of laws governing what sort of information is considered sensitive and how it must be stored and handled. For example, New York State restricts how you can use and store Social Security Numbers. If the agency implements a web-based tool, I suggest researching state rules regarding data privacy in the immediate state and any other state the agency could reasonably expect to have children from. Hypothetical example. If the agency is in Georgia, close to the border with Florida, the system should be compliant with Georgia and Florida state laws but not Louisiana state laws unless there is some reason to believe the agency is likely to work with children or adults from that state.

There are also separate laws and regulations for agencies handling child welfare information such as court documents, ICPC information, etc.

Note - I am a consultant that helps states with child welfare problems. One of my many hats include web-design. I felt like I should chime in with my .02 cents.

---

