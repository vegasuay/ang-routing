# AngRouting

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 8.3.8.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).

## Steps To Create Apps
create an Angular 8 application for this Routing & Navigation example by typing this command.
```bash
ng new angular-routing
```

we need to create the new components by type this command to generate it using Angular Schematics.
```bash
ng g component Home
ng g component About
ng g component Privacy
ng g component Terms
```

Edit `src/app/app-routing.module.ts` to import new components and add to route variable.
Install end import bootstrap style
```bash
npm install --save @ng-bootstrap/ng-bootstrap
```
Next, we have to modify the `src/app/app.component.html` file to replace all HTML tags except <router-outlet></router-outlet> tag.

### Angular Wildcard Route

To handle invalid URL navigation error, you can redirect the entire undefined router by the wildcard route that defines with two asterisks "**".

```bash
ng g component PageNotFound
```

Import that component in `src/app/app-routing.module.ts` file.

### Angular Routing & Navigation for Modular Web Application

add two new models using these commands:

```bash
ng generate module articles/articles --module app --flat --routing
ng generate module products/products --module app --flat --routing
```

Next, we will add the list and details views to each module.

```bash
ng g component articles/articles
ng g component articles/article-details
ng g component products/products
ng g component products/product-details
```

## the structure

```bash
|-- app
|   |-- about
|   |   |-- about.component.html
|   |   |-- about.component.scss
|   |   |-- about.component.spec.ts
|   |   |-- about.component.ts
|   |-- app-routing.module.ts
|   |-- app.component.html
|   |-- app.component.scss
|   |-- app.component.spec.ts
|   |-- app.component.ts
|   |-- app.module.ts
|   |-- articles
|   |   |-- article-details
|   |   |   |-- article-details.component.html
|   |   |   |-- article-details.component.scss
|   |   |   |-- article-details.component.spec.ts
|   |   |   |-- article-details.component.ts
|   |   |-- articles
|   |   |   |-- articles.component.html
|   |   |   |-- articles.component.scss
|   |   |   |-- articles.component.spec.ts
|   |   |   |-- articles.component.ts
|   |   |-- articles-routing.module.ts
|   |   |-- articles.module.ts
|   |-- home
|   |   |-- home.component.html
|   |   |-- home.component.scss
|   |   |-- home.component.spec.ts
|   |   |-- home.component.ts
|   |-- page-not-found
|   |   |-- page-not-found.component.html
|   |   |-- page-not-found.component.scss
|   |   |-- page-not-found.component.spec.ts
|   |   |-- page-not-found.component.ts
|   |-- privacy
|   |   |-- privacy.component.html
|   |   |-- privacy.component.scss
|   |   |-- privacy.component.spec.ts
|   |   |-- privacy.component.ts
|   |-- products
|   |   |-- product-details
|   |   |   |-- product-details.component.html
|   |   |   |-- product-details.component.scss
|   |   |   |-- product-details.component.spec.ts
|   |   |   |-- product-details.component.ts
|   |   |-- products
|   |   |   |-- products.component.html
|   |   |   |-- products.component.scss
|   |   |   |-- products.component.spec.ts
|   |   |   |-- products.component.ts
|   |   |-- products-routing.module.ts
|   |   |-- products.module.ts
|   |-- terms
|       |-- terms.component.html
|       |-- terms.component.scss
|       |-- terms.component.spec.ts
|       |-- terms.component.ts
|-- assets
|-- environments
|   |-- environment.prod.ts
|   |-- environment.ts
|-- favicon.ico
|-- index.html
|-- main.ts
|-- polyfills.ts
|-- styles.scss
|-- test.ts
```

## Angular Route Parameters

Open and edit `src/app/articles/articles-routing.modules.ts` then add these imports.

```bash
import { ArticlesComponent } from './articles/articles.component';
import { ArticleDetailsComponent } from './article-details/article-details.component';
```

Add the routes for those components.

```bash
const routes: Routes = [
  { path: 'articles', component: ArticlesComponent },
  { path: 'article/:id', component: ArticleDetailsComponent }
];
```

Edit `src/app/articles/articles/articles.component.html` then add this [routerLink] to the anchor.

```html
<a [routerLink]="['/article', article.id]" class="btn btn-success btn-lg">Show Details</a>
```

Next, add that article object to `src/app/articles/articles/articles.component.ts` before the constructor.

article = {
  id: 100,
  title: 'How to make router & navigation in Angular 8',
  author: 'Didin J.',
  description: 'A complete tutorial about creating router and navigation in the Angular 8 Web Application'
};

To read the params that sent from the articles view, open and edit `src/app/articles/article-details/article-details.component.ts` then add this import of ActivatedRoute.

```
import { ActivatedRoute } from '@angular/router';
Inject that module to the constructor.
```

constructor(private activatedRoute: ActivatedRoute) {}
Read the ID from the route params using ActivatedRoute inside the constructor bracket.

```
this.id = this.activatedRoute.snapshot.params.id;
```

Open and edit `src/app/articles/articles/article-details.component.html` then change the HTML tags to these lines of HTML tags.

```
<h1>The Details of Article with an ID: {{id}}</h1>
```