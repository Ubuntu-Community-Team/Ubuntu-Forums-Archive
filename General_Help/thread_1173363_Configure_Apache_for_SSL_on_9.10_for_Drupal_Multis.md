---
title: "Configure Apache for SSL on 9.10 for Drupal Multisite"
date: 2009-05-29
forum: General Help
---

### Post by howardjacobson on 2009-05-29
I am struggling to get SSL working on my self-hosted Ubuntu 9.10 server for use with one of several Drupal sites running in a Drupal multi-site configuration.  I have the crt and key files properly saved and with proper reading permissions.  All of my Drupal sites are in /var/www/html.  Below is my default-ssl file from /etc/apache2/sites-available.

When I try to reach the site for which I have purchased the SSL certificate, I can go to [https://www.site.com](https://www.site.com), but if I try to reach any other URL (e.g., [https://www.site.com/user](https://www.site.com/user)), I get a 404 Not Found error.  I can reach any part of the site if I just use [http://.](http://.)

What I want is to enable the Secure Pages module in Drupal so that just some of the pages in my site require / use SSL.

Thanks for any help.

**** default-ssl file ****

```

<IfModule mod_ssl.c>
<VirtualHost *:443>

        DocumentRoot "/var/www/html"
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

        ErrorLog /var/log/apache2/acaiteamnc_error.log
        LogLevel warn

        CustomLog /var/log/apache2/ssl_access.log combined
        SSLEngine on
        SSLCertificateFile /etc/ssl/certs/www.acaiteamnc.com.crt
        SSLCertificateKeyFile /etc/ssl/private/acaiteamnc.key
        SSLCertificateChainFile /etc/ssl/certs/sf_bundle.crt

        SSLOptions +StrictRequire
        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>

        BrowserMatch ".*MSIE.*" \
                nokeepalive ssl-unclean-shutdown \
                downgrade-1.0 force-response-1.0

</VirtualHost>
</IfModule>

```

---

