<template>
	<ion-page>
		<ion-header :translucent="true">
			<ion-toolbar>
				<ion-title>Inbox</ion-title>
			</ion-toolbar>
		</ion-header>

		<ion-content :fullscreen="true">
			<ion-refresher slot="fixed" @ionRefresh="refresh($event)">
				<ion-refresher-content></ion-refresher-content>
			</ion-refresher>
			<ion-list>
				<MessageListItem v-for="message in messages" :key="message.id" :message="message" />
			</ion-list>
		</ion-content>
	</ion-page>
</template>

<script>
import { IonContent, IonHeader, IonList, IonPage, IonRefresher, IonRefresherContent, IonTitle, IonToolbar } from "@ionic/vue";
import MessageListItem from "@/components/MessageListItem.vue";
import { getMessages } from "@/data/messages";

export default {
	name: "Home",
	data() {
		return {
			messages: getMessages(),
		};
	},
	methods: {
		refresh: (ev) => {
			setTimeout(() => {
				ev.detail.complete();
			}, 3000);
		},
	},
	components: {
		IonContent,
		IonHeader,
		IonList,
		IonPage,
		IonRefresher,
		IonRefresherContent,
		IonTitle,
		IonToolbar,
		MessageListItem,
	},
};
</script>
