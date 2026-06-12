---
title: "Cannot read ICEauthority file"
date: 2005-07-04
forum: Desktop Environments
---

### Post by ssck on 2005-07-04
Hi ALL,

Just some clarification.

I installed guarddog.And then uninstalled it.The next time when I tried to log into my gnome session, I encountered the above error.Why is this so ? What is the purpose of the file ?

The only way I could fix it (thanks to another thread on the same error) was to delete the file.

Could someone explain ?

To someone who is new to linux, it sure is scary if you can't login to your session.

Thanks.

---

### Post by jarrett.wold on 2005-07-06
Everything in Linux is centered around permissions, as is the rest of the *nix world.  As such, your ICEAuthority file more than likely had it's permissions set to some other user (likely root).  As such your normal user account cannot access files entirely owned by root.  

This usually happens because you are running an application using sudo (root), and it modifies the file.

ICE is a protocol specification that was put out by X Consortium.

Here's the overview from the ICE specification:

"Most protocols need mechanisms for authentication, for version
negotiation, and for setting up and taking down connections. There are also cases where the same two parties need to talk to each other using multiple protocols. For example, an embedding relationship between two parties is likely to require the simultaneous use of session management, data transfer, focus negotiation, and command notification protocols. While these are logically separate protocols, it is desirable for them to share as many pieces of implementation as possible.

The Inter-Client Exchange (ICE) protocol provides a generic framework for building protocols on top of reliable, byte-stream transport connections. It provides basic mechanisms for setting up and shutting down connections, for performing authentication, for negotiating versions, and for reporting errors. The protocols running within an ICE connection are referred to here as subprotocols. ICE provides facilities for each subprotocol to do its own version negotiation, authentication, and error reporting. In addition, if two parties are communicating using several different subprotocols, ICE will allow them to share the same
transport layer connection."

---

### Post by ssck on 2005-07-06
[QUOTE=jarrett.wold]Everything in Linux is centered around permissions, as is the rest of the *nix world.  As such, your ICEAuthority file more than likely had it's permissions set to some other user (likely root).  As such your normal user account cannot access files entirely owned by root.  

This usually happens because you are running an application using sudo (root), and it modifies the file.

ICE is a protocol specification that was put out by X Consortium.

Here's the overview from the ICE specification:

"Most protocols need mechanisms for authentication, for version
negotiation, and for setting up and taking down connections. There are also cases where the same two parties need to talk to each other using multiple protocols. For example, an embedding relationship between two parties is likely to require the simultaneous use of session management, data transfer, focus negotiation, and command notification protocols. While these are logically separate protocols, it is desirable for them to share as many pieces of implementation as possible.

The Inter-Client Exchange (ICE) protocol provides a generic framework for building protocols on top of reliable, byte-stream transport connections. It provides basic mechanisms for setting up and shutting down connections, for performing authentication, for negotiating versions, and for reporting errors. The protocols running within an ICE connection are referred to here as subprotocols. ICE provides facilities for each subprotocol to do its own version negotiation, authentication, and error reporting. In addition, if two parties are communicating using several different subprotocols, ICE will allow them to share the same
transport layer connection."[/QUOTE]


thanks for the explanation ... the problem happened after i installed and uninstalled guarddog ....

---

