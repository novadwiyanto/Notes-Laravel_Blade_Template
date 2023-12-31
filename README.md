# Laravel Blade Template
---

<br>

## HTML Encoding

`{{$variable}}` : Menggunakan htmlspecialchars()

`{!!$variable!!}` : Tanpa htmlspecialchars()

---

<br>

## Disabled Blade

`@{{$eko}}` : output {{$eko}}

`@verbatim -- @ endverbatim`

---

<br>

## If Statement

`@if() - @elseif() - @else() - @endif`

---

<br>

## Unless Statement

Kebalikan dari if statement. Dieksekusi apabila bernilai false

`@unless($var) - @endunless`

---

<br>

## Isset dan Empty

`@isset($var) - @endisset` : Apakah variabel ada dan tidak bernilai null

`@empty($var) - @endempty` : Apakah variabel merupakan array kosong

---

<br>

## Env

`@env("*testing") - @endenv`

`@env(["*testing", "*testing2"]) - @endenv`

---

<br>

## Switch Statement

`@switch - @case - @break - @default`

---

<br>

## For Loop

`@for() - @endfor`

`@foreach() - @endforeach`

`forelse() - @empty - @endforelse`

---

<br>

## RAW PHP

`@php - @endphp`

---

<br>

## While Loop

`@while() - @endwhile`

---

<br>

## Loop Variable

`@loop->index`

`@loop->iteration`

`@loop->remaining`

`@loop->count`

`@loop->first`

`@loop->last`

`@loop->even`

`@loop->odd`

`@loop->depth`

`@loop->parent`

---

<br>

## CSS Class

```
<head>
    <style>
        .red {
            color: red;
        }

        .bold {
            font-weight: bold;
        }
    </style>
</head>

<body>
@foreach($hobbies as $hobby)
    <li @class(["red", "bold" => $hobby["love"]])>{{$hobby['name']}}</li>
@endforeach
</body>
```

---

<br>

## Include

`@include('*namefile')`

`@include("header", ["title" => "Home Page"])`

---

<br>

## Include

`@includeWhen($user['owner'], 'header-admin')` : Kondisi true

`@includeUnless($user['owner'], 'header-admin')` : Kondisi false

---

<br>

## Each dan Once

```
// User file
@once
    <style>
        .red {
            color: red;
        }
    </style>
@endonce

<h1>{{$user['name']}}</h1>

<ul>
    @foreach($user['hobbies'] as $hobby)
        <li class="red">{{$hobby}}</li>
    @endforeach
</ul>

```
```
<body>
@each("user", $users, "user")
</body>
```

---

<br>

## Form

`@checked(kondisi)`

`@selected(kondisi)`

`@disabled(kondisi)`

`@readonly(kondisi)`

`@required(kondisi)`

```
<input type="checkbox" @checked($user['premium']) value="Premium"/> <br/>
<input type="text" value="{{$user['name']}}" @readonly(!$user['admin'])/> <br/>
```

---

<br>

## CSRF

---

<br>

## Error

```
@error("*key")
<p>{{$message}}</p>
@enderror
```

---

<br>

## Stack

```
@push("script")
    <script src="first.js"/>
@endpush

@push("script")
    <script src="second.js"/>
@endpush

@prepend("script")
    <script src="third.js"/>
@endprepend

@stack("script")
```

---

<br>

## Template Inheritance

```
// Parent Layout
@yield("title")
@yield("header")
```
```
// Child Layout
@extends("parent)

@section("title", "Home Page")

@section("header")
    <p>Deskription</p>
@endsection
```

Show Directive

```
// Parent Layout
@yield("title")
@section("header")
    <p>Deskription</p>
@show
@section("content")
    <p>Deskription</p>
@show
```
```
// Child Layout
@extends("parent)

@section("title", "Home Page")

@section("header")
    @parent
    <p>Deskription</p>
@endsection

@section("content")
    <p>Deskription</p>
@endsection
```

---

<br>

## Service Injection

`@inject(variable, service)` : Untuk mengambil object dari Service Container

```
@inject('service', 'App\Services\SayHello')
<h1>{{ $service->sayHello($name)  }}</h1>
```

---

<br>

## Optimizing Template

`php artisan view:cache`

`php artisan view:clear`

---

<br>

## Inline Blade Template

---

<br>

## Extending Blade

---

<br>

## Custom Echo Handler
