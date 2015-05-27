---
layout: post
title: Getting Started with Ansible Module Development on Mac OS X
---
<div class="message">
Prerequisite knowledge:
  <ul>
    <li>You have a working understanding of Ansible (i.e. You've created a playbook.)
        If you don't/haven't, see:
        <a href="http://docs.ansible.com/intro.html">http://docs.ansible.com/intro.html</a></li>
    <li>You know how to use git and github.  You know what github flow is.  
        If you don't, see: <a href="https://guides.github.com">https://guides.github.com</a></li>
  </ul>
</div>

[Ansible](http://ansible.com) is great.

Sometimes though you may need to improve on modules, or patch them, or just
create new ones.  

Here's what I did (and would do again) to get started:

* First, go to the IRC channel on freenode (#ansible-devel) and ansible
development group (<https://groups.google.com/d/forum/ansible-devel>)
to make sure someone isn't already working on the feature.
I would also browse/search the issues on the github page to see if someone has
a related outstanding issue.  If you don't know what IRC/freenode are start here: <https://freenode.net/using_the_network.shtml>
* If at this point you still want to proceed...read this: <https://docs.ansible.com/developing_modules.html>
* Clone the main ansible repo.  <https://github.com/ansible/ansible>
* Setup your environment to run against the ansible source you just cloned.  
{% highlight bash %}
source ansible/hacking/env-setup
{% endhighlight %}
* Fork the repo where the module currently lives, either
`https://github.com/ansible/ansible-modules-core` or
`https://github.com/ansible/ansible-modules-extras`.  If you're developing a new
module you most likely want to put it in `ansible-modules-extras`.
* Create a branch to work in.
* Setup your environment to run against these module locations first (if you didn't
do this step ansible would look at the main ansible directory cloned above first.)
{% highlight bash %}
export ANSIBLE_LIBRARY=~/ansible-modules-core:~/ansible-modules-extras
{% endhighlight %}
* Setup an ansible playbook that uses the module you want to change.
* Confirm the playbook runs before you make changes.
* Make changes to the module.  
* Confirm the changes work.
* Commit your changes to your branch.
* Push your changes to your fork.
* Open a PR.  

Note: There is a `test-module` script that you can use to execute a module
without writing a playbook.  See <http://docs.ansible.com/developing_modules.html#testing-modules>

In my case, the module I was changing didn't work with the `test-module` script,
so I used the steps I outlined above.
