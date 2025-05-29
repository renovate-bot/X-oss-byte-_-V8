# Copyright 2021 the V8 project authors. All rights reserved.
# Use of this source code is governed by a BSD-style license that can be
# found in the LICENSE file.

workspace(name = "v8")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

http_archive(
    name = "bazel_skylib",
    sha256 = "1c531376ac7e5a180e0237938a2536de0c54d93f5c278634818e0efc952dd56c",
    urls = [
        "https://github.com/bazelbuild/bazel-skylib/releases/download/1.0.3/bazel-skylib-1.0.3.tar.gz",
        "https://mirror.bazel.build/github.com/bazelbuild/bazel-skylib/releases/download/1.0.3/bazel-skylib-1.0.3.tar.gz",
    ],
)

load("@bazel_skylib//:workspace.bzl", "bazel_skylib_workspace")

bazel_skylib_workspace()

http_archive(
    name = "rules_python",
    sha256 = "690e0141724abb568267e003c7b6d9a54925df40c275a870a4d934161dc9dd53",
    strip_prefix = "rules_python-0.40.0",
    url = "https://github.com/bazelbuild/rules_python/archive/0.40.0.tar.gz",
)

load("@rules_python//python:pip.bzl", "pip_install")

pip_install(
    name = "v8_python_deps",
    extra_pip_args = ["--require-hashes"],
    requirements = "//:bazel/requirements.txt",
)

new_local_repository(
    name = "com_googlesource_chromium_zlib",
    build_file = "bazel/BUILD.zlib",
    path = "third_party/zlib",
)

bind(
    name = "zlib",
    actual = "@com_googlesource_chromium_zlib//:zlib",
)

bind(
    name = "zlib_compression_utils",
    actual = "@com_googlesource_chromium_zlib//:zlib_compression_utils",
)

new_local_repository(
    name = "com_googlesource_chromium_icu",
    build_file = "bazel/BUILD.icu",
    path = "third_party/icu",
)

bind(
    name = "icu",
    actual = "@com_googlesource_chromium_icu//:icu",
)

new_local_repository(
    name = "com_googlesource_chromium_base_trace_event_common",
    build_file = "bazel/BUILD.trace_event_common",
    path = "base/trace_event/common",
)

bind(
    name = "base_trace_event_common",
    actual = "@com_googlesource_chromium_base_trace_event_common//:trace_event_common",
)
