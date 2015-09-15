===============================
spousefriendly
===============================

.. image:: https://img.shields.io/pypi/v/spousefriendly.svg
        :target: https://pypi.python.org/pypi/spousefriendly


Be nice to your spouse - give your command line scripts some GUI feedback when needed.

* Free software: ISC license
* Documentation: https://spousefriendly.readthedocs.org.

Motivation
----------

Developer types usually like to run scripts from a command line. In addition,
for these kind of Python scripts, if something goes wrong, the easiest thing to
do is let it fail 'ungracefully', at which point you get a helpful stacktrace on
the screen. And if it goes well, it should just exit without printing anything.

For your spouse or friend who just wants to double click an icon, both these
behaviours will be very confusing. They normally want confirmation that it
worked and is finished, and if it doesn't it should show some kind of nice error
message.

This package provides some simple wrappers (normally context managers) so that
you can get the best of both worlds.

Basic usage
-----------

Take a typical script::

    def main():
        # Stuff here


    if __name__ == '__main__':
        main()


Simply wrap the call to main in a spousefriendly.friendly_success_and_failure with block::


    import spousefriendly

    if __name__ == '__main__':
        with spousefriendly.friendly_success_and_failure():
            main()


If running from a terminal, there will be no change in behaviour. From a GUI,
however (e.g. launched from a file manager), upon exit there will be a success
message, or a failure message if appropriate.


Detailed usage
--------------

``friendly_success_and_failure`` composes two context managers::

  spousefriendly.friendly_success(success_message='Optional success message')

  spousefriendly.friendly_failure(failure_message='Optional failure message')

Both ``success_message`` and ``failure_message`` can also be passed to
``friendly_success_and_failure`` as keyword arguments. Sensible defaults are
used if not supplied.


Limitations
-----------

Obviously, the context managers can't protect against anything that happens
outside their scope (e.g. import errors etc.).


TODO
----

Windows support! This is the most obvious one. Since I don't use Windows, I'm
not in a position to test this. I've put some rudimentary things in, but it
probably doesn't work.