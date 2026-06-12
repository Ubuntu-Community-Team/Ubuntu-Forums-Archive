---
title: "Getting Evolution to connect to LDAP server"
date: 2008-05-08
forum: Desktop Environments
---

### Post by misja on 2008-05-08
I have been trying to get Evolution to connect to my company's LDAP server, without sucess.
What I did was: I went to 'Contacts', chose 'new Address book', in the dialog I chose 'on LDAP server', and filled in the port (3268 or 389) and host address for the server. The server seems to be a Microsoft LDAP server btw.

When I then choose 'find possible search bases' I get a little list with options. However whichever one I choose, when I do a search for contacts I either get no result at all or I get a popup with the message 'Unable to perform Search. This query did not complete succesfully'.

I really don't know why this query did not end succesfully, I also don't have a clue as to how to connect my Evolution to the LDAP server.
What could I have missed?

PS I am trying this on an Ubuntu 8.04 machine.

---

### Post by mcapozzi on 2008-05-08
It is easier to use the "Global Address List / Active Directory" option under "Receiving Options" in Account Editor assuming you are setting up an Exchange account.

If you use that, all you have to enter is the IP or FQDN of your Domain Controller.  You won't have to mess around with LDAP search strings.

-Mike

---

### Post by misja on 2008-05-08
Thanks, but I don't have any such option under the 'receiving options' tab in the account manager, nor under any other tab ...

Could you tell me where I could find this "Global Address List / Active Directory" option? Or am I using the wrong version of Evolution? (2.12.1)

---

### Post by mcapozzi on 2008-05-08
I am running Evolution 2.22.1.  The setting is located in your Exchange account preferences.

-Mike

---

### Post by misja on 2008-05-08
I log in via IMAP, so that's why I don't have those Exchange settings. Logging in using 'Exchange Server' does not get me past the authorisation.

So I guess using the Exchange settings is not an option, I'll have to deal with the LDAP settings in the contacts tab ..

---

### Post by mcapozzi on 2008-05-08
Ahhh, you are having trouble with connecting to exchange.  What are you using as the username.  I had trouble connecting with domain\username, I had better luck with username@domain.

If you can't get Exchange to work (which it should), you can try a seach string such as:

cn=Users,dc=domainname,dc=DNSSuffix


-Mike

---

### Post by tomvoss on 2011-02-15
I wrote up [_detailed step-by-step instructions for connecting Evolution to Exchange 2007 Global Address List via LDAP_]("http://tomvoss.blogspot.com/2011/01/connecting-evolution-to-exchange-2007.html").

---

