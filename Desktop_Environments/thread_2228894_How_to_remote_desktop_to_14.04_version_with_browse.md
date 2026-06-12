---
title: "How to remote desktop to 14.04 version with browser"
date: 2014-06-10
forum: Desktop Environments
---

### Post by shahin on 2014-06-10
I followed this tutorial [http://xmodulo.com/2013/09/access-vnc-remote-desktop-web-browser.html]("http://xmodulo.com/2013/09/access-vnc-remote-desktop-web-browser.html") and seem to be able to load the login page from my remote computer browser. But I can not log in. I get the noVNC page with a message stating: "Unsupported security types: 18". The vnc server messages say: 
127.0.0.1: SSL connection but '/home/.../noVNC/self.pem' not found
127.0.0.1: SSL connection but '/home/.../noVNC/self.pem' not found
127.0.0.1: SSL connection but '/home/.../noVNC/self.pem' not found
127.0.0.1: SSL connection but '/home/.../noVNC/self.pem' not found
127.0.0.1: SSL connection but '/home/..../noVNC/self.pem' not found
127.0.0.1: SSL connection but '/home/.../noVNC/self.pem' not found
127.0.0.1: SSL connection but '/home/..../noVNC/self.pem' not found
127.0.0.1 - - [10/Jun/2014 07:08:34] 127.0.0.1: Plain non-SSL (ws://) WebSocket connection
127.0.0.1 - - [10/Jun/2014 07:08:34] 127.0.0.1: Version hybi-13, base64: 'False'
127.0.0.1 - - [10/Jun/2014 07:08:34] 127.0.0.1: Path: '/websockify'
127.0.0.1 - - [10/Jun/2014 07:08:34] connecting to: localhost:5900

I kow pem is the extension for a certificate. I don't know how this is asking for a certificate when the connection is a straigh http. Some services do you ssl over http vs. https. But do I need to get the certificate in there myselft? How do I do that? or is the problem something else? 

I assume I am in the right group. If not, please do let me know what group I need to move this discussion to.

---

