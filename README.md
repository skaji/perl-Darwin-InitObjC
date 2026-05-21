# NAME

Darwin::InitObjC - initializes Objective-C runtime

# SYNOPSIS

    use Darwin::InitObjC;

    Darwin::InitObjC::maybe_init();

    my $pid = fork // die;
    if ($pid == 0) {
      do_something();
      exit;
    }
    wait;

# DESCRIPTION

Darwin::InitObjC initializes Objective-C runtime.

In macOS 13+, initialising Objective-C APIs in forked processes are treated as errors.
So you may see the following errors when executing your scripts:

    objc[80048]: +[NSString initialize] may have been in progress in another thread when fork() was called.
    objc[80048]: +[NSString initialize] may have been in progress in another thread when fork() was called. We cannot safely call it or ignore it in the fork() child process. Crashing instead. Set a breakpoint on objc_initializeAfterForkError to debug.

A workaround is to initilize Objective-C runtime before calling fork(2).

# SEE ALSO

https://bugs.ruby-lang.org/issues/14009

# ARTIFACT ATTESTATIONS

GitHub Artifact Attestations are generated for release tarballs uploaded to
CPAN. If you care about provenance for the uploaded tarballs, see:

[https://github.com/skaji/perl-Darwin-InitObjC/attestations](https://github.com/skaji/perl-Darwin-InitObjC/attestations)

# COPYRIGHT AND LICENSE

Copyright 2024 Shoichi Kaji <skaji@cpan.org>

This library is free software; you can redistribute it and/or modify
it under the same terms as Perl itself.
