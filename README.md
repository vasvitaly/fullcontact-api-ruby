FullContact Ruby Gem
====================
A Ruby wrapper for the [FullContact API](http://www.fullcontact.com/)

Changes
-------

0.6.2 - Update Faraday version to 0.9.0
0.6.0 - Removal of timeoutSeconds parameter. This parameter is automatically stripped from your request if included.

Installation
------------
    gem install fullcontact

Documentation
-------------
[http://rdoc.info/gems/fullcontact](http://rdoc.info/gems/fullcontact)

Usage Examples
--------------
```ruby
    require "fullcontact"

    # This could go in an initializer
    FullContact.configure do |config|
        config.api_key = "fullcontact_api_key_goes_here"
    end
	
    # Get information about an email address
    person = FullContact.person(email: "brawest@gmail.com")
    
    # Get information about an email address, organized by hashes vs. lists
    person2 = FullContact.person(email: "bart@fullcontact.com", style: "dictionary")
    
    # You can pass in any arbitrary parameters the Person API supports
    person3 = FullContact.person(email: "bart@fullcontact.com", style: "dictionary", webhookUrl: "https://...")
    
    # Get information about a twitter handle
    person4 = FullContact.person(twitter: "brawest")

    # Get information about a facebook username
    person5 = FullContact.person(facebookUsername: "bart.lorang")
    
    # Get information from a phone number
    person6 = FullContact.person(phone:13037170414)
    
    # Get information about a twitter and ensure a 30s socket open timeout and a 15s socket read timeout
    # Can throw a Faraday::Error::TimeoutError if timeouts are exceeded
    person7 = FullContact.person({:twitter => "brawest"}, {:request => {:timeout => 15, :open_timeout => 30}})

    # Get person's family_name
    puts person.contact_info.family_name
```
	
Contributions
-------------
- Michael Rose (Xorlev)
- Ian Fisher (i-taptera)
- Scott Watermasysk (scottwater)
- Stefano Fontanelli (stefanofontanelli)

Copyright
---------
Copyright (c) 2014 FullContact, Brandon West

See [LICENSE](https://github.com/brandonmwest/rainmaker/blob/master/LICENSE.md) for details.
